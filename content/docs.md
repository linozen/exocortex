---
title: Documentation
---

## Motivation

Overall, this entire project serves the goal of augmenting human intellect - a
notion popularized by the computer visionary Douglas @engelbart1962:

> By "augmenting human intellect" we mean increasing the capability of a man to
> approach a complex problem situation, to gain comprehension to suit his
> particular needs, and to derive solutions to problems. Increased capability in
> this respect is taken to mean a mixture of the following: **more-rapid
> comprehension**, **better comprehension**, **the possibility of gaining a
> useful degree of comprehension in a situation that previously was too
> complex**, **speedier solutions**, **better solutions**, and **the possibility
> of finding solutions to problems that before seemed insoluble**.
>
> And by "complex situations" we include the professional problems of diplomats,
> executives, social scientists, life scientists, physical scientists,
> attorneys, designers—whether the problem situation exists for twenty minutes
> or twenty years. We do not speak of isolated clever tricks that help in
> particular situations. We refer to a way of life in an integrated domain where
> hunches, cut-and-try, intangibles, and the human "feel for a situation"
> usefully co-exist with powerful concepts, streamlined terminology and
> notation, sophisticated methods, and high-powered electronic aids.

When I write **Exocortex**, I mean my very own high-powered electronic aid to
better make sense of the world around me. This system should be

- simple (turns out to be real difficult)
- well-documented (this is what this node is for)
- future-proof (always stick to plain-text markdown at the base)
- quick to add to (see [[docs#Input layer]])
- fun to process (see [[docs#Processing layer]])
- and quick to retrieve (see [[docs#Retrieval layer]])

As my Exocortex should never be tied to any particular tool or technology, it is
based at the core on plain-text markdown files on a regular file system. This is
to ensure that I can keep changing tooling around it freely while the core data
remains close to a widely recognized standard that many tools support.
Ultimately, the goal is to converge on a set of technologies that will remain
somewhat stable and hopefully keep the complexity dragons at bay (very
unlikely).

## Layers

### Input

At this layer I capture and curate (see [[curation]]) incoming information.
Information is committed to the system through these interfaces:

- Obsidian on my Laptop
- Neovim with Obsidian plugin -
  [Nix flake](https://github.com/linozen/nvim-flake)
- [Markor](https://github.com/gsantner/markor) (Android phone with
  [GrapheneOS](https://grapheneos.org/))

### Processing

At this layer, I refine and connect knowledge. It consists mainly of (re)writing
and organizing in this space, i.e. the Exocortex, and creating Anki cards.

In the future, this section will contain documentation for how I transform
material I read or watched to [[refs/index|reference notes]] or
[[concepts/index|concept notes]]. If I want to store something for the long-term
I add it to Anki. There I follow Michael Nielsen's
[advice](http://augmentingcognition.com/ltm.html) to have one big deck (which I
call `LTS`) for everything.

> [!warning] WIP
>
> This needs to be updated once my setup is a bit more settled

### Retrieval

This layer enables quick access to processed information. Publicly, I can
retrieve the information by using

- `Ctrl + K` on this website (https://exocortex.sehn.dev)
- or searching the `.md` files in the git forges that this project uses

Privately, I retrieve information via

- my very own wetware. I'm using Anki to get it there.
- full-text search using Neovim or Obsidian on the local file system of my phone
  of my laptop.
