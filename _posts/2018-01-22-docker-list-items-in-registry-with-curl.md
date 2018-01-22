---
layout: post
title: "Docker: Listing items in a basic auth registry with curl"
---
To get a list of all image names:

  curl -u username -X GET https://reg.example.com/v2/_catalog

You will be prompted for a password for the user by curl.

To get a list of all tags available on an image:

  curl -u username -X get https://reg.example.com/v2/some-image-name/tags/list
  
