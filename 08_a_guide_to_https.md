# A guide to HTTPS

## Index

- [A guide to HTTPS](#a-guide-to-https)
  - [Index](#index)
  - [Intro](#intro)
  - [FAQ](#faq)
    - [What do a HTTPS server require, and what about a HTTPS client?](#what-do-a-https-server-require-and-what-about-a-https-client)
    - [What is the certification file and key file means?](#what-is-the-certification-file-and-key-file-means)
    - [How to enable https in server side?](#how-to-enable-https-in-server-side)

## Intro

HTTPS basically is a technic to transport encrypted data via http. It require client and server do extra work but ensure user more security. 

## FAQ

Firstly, let's take some short **FAQ**: 

### What do a HTTPS server require, and what about a HTTPS client?

**The server**:

1.  A worked HTTP server and support HTTPS feature.
2.  A pair of files which is a validated certification file and a key file

**The Client**:

The client just need to support transport HTTPS pocket, no certification or key needed.

### What is the certification file and key file means?

### How to enable https in server side?

It's up to your server side software. 

If you use `nginx` as a server, you need to specific the **certification file** and **key file** in nginx's configuration.

If you use a server program written in yourself, you need to search the language reference to learn how to enable the HTTPS functionality.
