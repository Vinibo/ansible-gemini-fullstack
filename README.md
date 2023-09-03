# ansible-gemini-fullstack

## An easy way to self-hosting a Gemini capsule!
This playbook deploys a Gemini server and an Gemini-to-HTTP proxy in no time!
Make your capsule accessible for both Gemini browsers AND regular web browsers.

## What is Gemini
I cannot describe Gemini better than the Wikipedia article (https://en.wikipedia.org/wiki/Gemini_(protocol)) but here's my personal take.
Internet, as it was originally designed, aimed at sharing knowledge in the form of documents. Fast-forwarding a couple of decades, the current internet is more about for style than the content. You must have Javascript and CSS in order to have a functional website. And that clash with the original idea, where the document is the main element. If your web browser cannot read Javascript or CSS, chances are you won't be able to get the information you're looking for (either because ads gets in the way of content, or content being not properly ordered). Gemini aims to fix that. Your Gemini capsule contains only the content (text, images) and it's the client (and your preferences) that shapes the content you look at. This means that the content creator does not have to worry about the form-factor on which the content is consumed! Think about old computers, terminals, low-power devices, or e-readers!
In this era of cookies and centralization of the internet, Gemini feels like a breath of fresh air, and honestly, makes producing content fun again.

## What is a capsule?
A Capsule is the equivalent of a website. Simple as that!

## Components used
Agate is a simple Gemini server written in the Rust language. 
https://github.com/mbrubeck/agate

September is an Gemini-to-HTTP proxy written in Rust that lets regular web browsers access Gemini capsules.
https://github.com/gemrest/september

## Supported architectures
- x86-64
- ARMv7
- aarch

## Supported Operating systems
- Ubuntu
- Armbian

## How to deploy this playbook

### Install Ansible dependencies
`ansible-galaxy install -r requirements.yml`

### Execute your playbook on a server
`ansible-playbook -K -b site.yml -i inventories/hyena/inventory`

## FAQ
- Why does this playbook does not support RISC-V
    I originally wanted to deploy my capsule on a small RISC-V board I owned, the Sipeed Lichee RV. Unfortunately, both Agate and September are using a Rust cryptographic library that does not compile on this architecture (https://github.com/briansmith/ring).