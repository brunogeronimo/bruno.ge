---
title: "An introduction to Terraform"
date: 2020-10-06T12:05:52+02:00
summary: Let's learn a little bit about Terraform.
authors: [Bruno Geronimo]
reviewers: [Birgit Pohl, Carolina Robles, Eric Dallo, Ramon Andrade]
draft: true
---

When you opt-in for cloud computing, there are several ways to organize your infrastructure. You can simply create things on demand through the control panel of your cloud provider or, in some cases, create your own scripts to trigger cloud APIs. Options are endless. It depends on creativity, use-case and needs.

If you have a small infrastructure to take care of, a manual process with some documentation might be enough. If you need something more robust and controlled, an automated process can be the way.

When it comes to automation, it is also very important to think about maintainability, and it is hard to find a compromise between building a custom solution or using something popular. One option which is really helpful for me during my journey into the DevOps is [Terraform](https://www.terraform.io/).

## A little bit about Terraform

Terraform is an open-source [infrastructure as code](https://en.wikipedia.org/wiki/Infrastructure_as_code) software tool. Basically, it means that instead of using a control-panel or building your own scripts to create your infrastructure, you can use a cleaner syntax to declare the desired resource and Terraform will take care of building it, from static IPs and DNS entries to a Compute Engine machine and a Kubernetes cluster.

By using Terraform, you have lots of advantages. For example:

- The infrastructure is entirely backed-up
- The code is very flexible and easy to read
- It is versionable
- It makes everything easier to replicate your infrastructure to multiple environments
- Dependencies between resources are easier to visualize.

## It's time to ~~DUEL!!!~~ code

Let's take a look at some examples using Terraform.

### Using a static IP with a DNS entry pointing to it on Google Cloud

```
terraform { #1
  required_version = ">= 0.12"
}

provider "google" { #2
  project = "my-awesome-staging-server"
  region = "europe-west1-d"
  version = "2.14.0"
}

resource "google_compute_global_address" "staging" { #3
  name = "staging"
}

resource "google_dns_managed_zone" "staging" { #4
  name = "staging"
  dns_name = "bruno.works."
}

resource "google_dns_record_set" "staging" { #5
  project = "my-awesome-staging-server"
  managed_zone = google_dns_managed_zone.staging.dns_name

  name = "staging.bruno.works."
  type = "A"
  ttl  = 60

  rrdatas = [
    google_compute_global_address.staging.address
  ]
}
```

#### What is actually being defined here?

1. Restricts Terraform version to `0.12` or above
2. Defines global settings for all resources related to Google Cloud. On the example above, we're setting up the default project, default server region and also defining which provider version we want to use
3. Requests a static IP called `staging`
4. Creates a DNS managed zone, so we can create our DNS entries for the `bruno.works` domain
5. Creates a DNS entry type `A` named `staging.bruno.works` (on Google Cloud, the final dot on the string is mandatory) pointing to the static IP defined on step 3.

## Cool things about Terraform

- It identifies which resources are depending on other resources. For example: It doesn't make sense to try to create a DNS record if the managed zone is not created yet or if the static IP is not available by some reason. As we have attributes referring to those resources, they're automagically dependent from each other (see `managed_zone` and `rrdatas` attributes);
- When you deploy your infrastructure, it generates a `.tfstate` file. This file controls the status of all resources and, based on that, Terraform identifies which resources have to be updated, destroyed or created when you change your code;

This article is an introduction to Terraform. My idea is to create several others explaining from the basics how to define a complex infrastructure with the help of Terraform. If you can, please, give me some feedback about what you think of my way of writing, so I can use it to improve the next ones! :)

## References

- Terraform: https://www.terraform.io
- Infrastructure as code: https://en.wikipedia.org/wiki/Infrastructure_as_code
