---
title: Organizations | GitHub API
---

# Organizations

* TOC
{:toc}

## List your organizations

List organizations for the authenticated user.

    GET /user/orgs

### Response

<%= headers 200, :pagination => default_pagination_rels %>
<%= json(:org) { |h| [h] } %>

## List user organizations

If you make an unauthenticated call, you will list all [public memberships](https://help.github.com/articles/publicizing-or-concealing-organization-membership) in organizations for any user. If you make an authenticated call, you will also list hidden memberships in organizations, but only for the currently authenticated user.

    GET /users/:username/orgs

### Response

<%= headers 200, :pagination => default_pagination_rels %>
<%= json(:org) { |h| [h] } %>

## Get an organization

    GET /orgs/:org

### Response

<%= headers 200 %>
<%= json(:full_org) %>

## Edit an organization

    PATCH /orgs/:org

### Input

Name | Type | Description
-----|------|--------------
`billing_email`|`string` | Billing email address. This address is not publicized.
`company`|`string` | The company name.
`email`|`string` | The publicly visible email address.
`location`|`string` | The location.
`name`|`string` | The shorthand name of the company.

### Example

<%= json \
    :billing_email => "support@github.com",
    :blog     => "https://github.com/blog",
    :company  => "GitHub",
    :email    => "support@github.com",
    :location => "San Francisco",
    :name     => "github"
    %>

### Response

<%= headers 200 %>
<%= json(:private_org) %>
