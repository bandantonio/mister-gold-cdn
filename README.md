# mister-gold-cdn

Static resources (css, js, etc.) from [Mister Gold](https://mister-gold.pro) blog.

[![mister-gold-cdn npm](https://img.shields.io/npm/v/mister-gold-cdn.svg?style=flat-square)](https://www.npmjs.com/package/mister-gold-cdn) [![mister-gold-cdn Downloads](https://img.shields.io/npm/dm/mister-gold-cdn.svg?style=flat-square)](https://www.npmjs.com/package/mister-gold-cdn)

[![NPM](https://nodei.co/npm/mister-gold-cdn.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/mister-gold-cdn/)

## Introduction

The idea of having a detached location (a repository) with static files is based on separating requests when loading a website. In other words, it is better to have 5 different places for loading resources from, rather than just one place that holds all the resources.

When there is only one place that holds all the resources, the requests go consecutively in queue, which means that it is impossible to load a specific resource, until all the preceding requests are loaded. When there are multiple locations, the requests can go in parallel, without blocking each other, which reduces the time taken to load the whole site. As research show, the average load time can be reduced up to 30-50%.

## Solution

This solution uses GitHub repository to store the static files that are published as a [npm](https://github.com/npm/npm) package and then distributed via [jsDelivr](https://www.jsdelivr.com/) Content Delivery Network. The links to the distributed files are added to the template files of my blog, where they are actually called from. To make the CDN even more efficient and decrease the number of concurrent requests, all non-critical files were combined into one. Furthermore, I used subsetting for resources like FontAwesome to get rid of excessive (and unused) portions of code.

### Results

These results were received on my [personal blog](https://mister-gold.pro) that is powered by [Pelican Static Site Generator](https://blog.getpelican.com/) and hosted on GitLab Pages.

Parameter          |  Before   | After                             | Profit
:------------------|:---------:|:---------------------------------:|:-----:|
number of requests | 12        | 9 (can be further decreased to 7) | 25%   |
load time          | 1.66 s    | 366 ms                            | 78%   |
page size          | 143.3 Kb  | 88.8 Kb                           | 38%   |
performance grade  | 86        | 92                                | 7%    |

I assume that the same (or even greater) results can be acheived on other SSG (e.g. Jekyll, Hugo or Hexo) or CMS (e.g. WordPress), because there are bunch of files that can be easily combined and distributed over a CDN.

## Contribution

The implemetation of my "static network" is stupidly simple and I suppose it is not as great as it could be, so if there are some better, more efficient or elegant approaches, your ideas are welcome and appreciated! Feel free to create an [issue](./issues) and share your thoughts. Let's do some cool stuff together!
