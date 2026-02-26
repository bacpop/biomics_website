# self.dna

Alessandro Lussana¹, Alistair Rust¹, Erin Chung², Filipe Rodrigues³, Pedro Suzano⁴

1. EMBL-EBI, Hinxton, UK
2. EMBL, Heidelberg, Germany
3. AccelBio, Cantanhede, Portugal
4. Universidade de Lisboa, Lisbon, Portugal

## Project overview

**self.dna** is a personal genomics app. Differently from commercial alternatives it is open-source and self-hosted, ensuring users have full control over their genetic data and the way they are processed.

It adopts a modular design that allows the community to develop custom analysis modules. This makes it possible to unlock new insights based on ever advancing capabilities in genome analysis. At startup, the app will only load the modules the user needs.

Deploying **self.dna** involves cloning a GitHub repository to build the Docker container where the app will run: 

![selfdna_0](/images/selfdna_0.png)

Currently, **self.dna** accepts the upload of a Variant Call Format (VCF) file. The VCF is stored and used to build a relational database, which can be read and written by the analysis modules. Such database persists on disk and can be ported to different instances of the app.

* 🌐 [DEMO](https://selfdna.alussana.net)
* 💻 [Repository for the Hackaton](https://github.com/alussana/self.dna-biomics) 

## Hackaton achievements

We made significant progress in transforming **self.dna** from a simple proof of concept demo, based on a single script, into a maintainable, community-driven piece of software. The main changes involved:

* **Fast input ingest:** Better support for large uploads, such as a human genome, with better utilization of the available cores.
* **Variants reference annotation:** Core module to add variant annotation information from the [GENCODE](https://www.gencodegenes.org) project. This populates the *annotations* table of the persistent database, to be used in many downstream analysis.
* **Modular architecture:** Dynamic discovery of the analysis modules present at startup, determining the layout of the dashboard.
  * Each valid module will cause the creation of a tab in the dashboard
  * Each module is a Class
  * Containing the attribute `tab_name`
  * And the method `render()`
  
  The following is a screenshot of the **self.dna** dashboard displaying 5 tabs/functionalities, in addition to the default tabs "Upload VCF" and "About".

![selfdna_1](/images/selfdna_1.png)

## TODO

This hackaton generated a strong momentum in the development of this project. Natural next steps to finalize the work will be:

* Merge branches and refine the main codebase
* Write community guidelines and documentation for development of the analysis modules
* Write more core modules (e.g. non-sense variant mapping, ClinVar analysis)
* Consider port in WebAssembly?
