---
layout: post
title: Favorite icon helper
---

Anyway, here it is

<typo:code lang="ruby">
  # Generate the image tag with the favorite icon of a given URL
  # Returns an empty string in case of failure
  def favicon_tag(url)    
    require 'open-uri'
    require 'rexml/document'
    require 'net/http'
    
    uri = URI.parse(url) rescue nil
    f = open(uri).read() rescue nil
    doc = REXML::Document.new(f) rescue nil
    href = REXML::XPath.first(doc, "//link[@rel='shortcut icon']/@href").value rescue "/favicon.ico"
    # try to get it
    favicon = uri + href
    h = Net::HTTP.new(favicon.host, favicon.port)
    r,d = h.head(favicon.path) rescue nil
    if r.code == "200"
      return image_tag favicon.to_s
    else
      return ''
    end
  end
</typo:code>
