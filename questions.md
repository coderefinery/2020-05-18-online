## Questions, answers, and feedback


### Reproducible Research lesson

#### Issues with reproducibility

Computer programs are expected to produce the same output for the same inputs. Is that true for research software?

Can you give some examples? What can we do about it?

- Yes I had plenty of experiences with that. Specially when work platforms are changing. But I found it easiest when writer shares a requirements.txt file with specifying their version. Also when they share code in github instead of sharing the files it was better because they maintained the code. Even with requirements.txt it could be impossible to reproduce because the versions that was used before are not accesible anymore.
- Published data and code is inclomplete, so one can reproduce parts of a study but not everything.
- We use an article in a computer lab that is not reproducible. 
- I have not been able to recreate the environment because of different software versions. Published articles lack info and even contacting the authors could not recreate what they did.  
- Mainly issues with code written be previous researchers, who did not document their work. They also forgot to include code dependencies to other scripts from them, other people, repositories, etc. I usually had to figure out the dependencies myself.
- Yes, many times. Trying to re-run the same analysis published in some paper but lacking not only version information but also parameters that are required. 
- Not being able to run a published software on the first place.
- I read wonderful studies, but I have no idea how to do that study or get to their results.
- How many people hope that no one cares enough to try, so you don't have to figure out what you actually did?
- For software I often find articles who doesn't even list the versions or environments in the methods section of the article. I don't quite understand how this passes review.
- We have many example of research codes that have been one use only. 
- we had an exercise once reproducing a full article during my masters and it gave a lot of insight into their workflow and what can differ when you do it yourself, and I understood much more after  having gone through it which I felt should be more trnsparent in the article itself
- sometimes it's such a small thing as some sofware having randoms seeds, without specifying which one, making reproducing the results impossible
- my group has recently published an article thath points out that one out of five studies in metagenomics does not provide data (other problems are included): https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.3000698 
- codes which are owned by a third party (company or research group)



#### Do you share any other research outputs besides published articles and possibly source code?

- I started getting DOIs for source code releases and data
- Yes, some files and we started to share the code too. However, it has been a problem to push for shared data/code with my previous supervisor
- Yes, we share a lot of reserch code 
  - would you like to show a link? I would be interested to see how this is done and learn.
- Yes, curves with high resolution that can not fit in article, produced data from raw data.
- Not yet, but I am preparing my current work to be open
- No, even my collaboration partner did not share his code with me. But he used pieces of Matlab, everything was in pieces. I wrote everything in Python. His programming skills are not good.
- Have shared sequence data (primary data), but also noticed that many researchers are somewhat hesitant to share since they don't want to give up an edge, or allow others to gain advantage from our data.
- Github repositories
- Yes, though source code was required by the journal. 
- Codes are owned by industrial partners. This cause lots of problems. 
  - How are you solving this problem?
- I often collaborate with other groups that are good in sharing data because they use common platforms for metagenomics but the problem is about sharing metadata and, most of all, sharing code 

#### General questions, motivation/organizing/sharing

- Could you explain a little about LICENSE types and how to find the most appropriate to our work?
    - We scheduled a [lesson on  software licenses](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/master/talk.md) later today
- What is the difference between zenodo and the sandbox?
  - On the "real" service once you get a DOI for a record, the record cannot easily be removed (this is the point of DOIs). You can still modify the metadata though. So the advantage of "practicing" on the sandbox is that one can make mistakes and it does not generate any persistent records.
- Will this also archive submodules for the github repo?
  - The usual zip download of github does not include submodules...
  - It seems not: https://github.com/zenodo/zenodo/issues/1036
- Can I get a DOI for an existing release or do I have to do a new one? 
  - Yes, you certainly can
  - Zenodo will automatically create DOIs for releases made after the repository has been enabled and the question is about the "past" releases I guess which will not be automatically created. So how does it work "yes, you certainly can" (above)? For past releases I would do it manually or using Zenodo API.
      - Yes, zenodo does not seeem to find old releases
      - Guess I can "upload" that directly?
        - Yes, this is always possible.
- git question: How to share code snippet on github in a seperate folder rather than making a repository? I tried it on bitbucket but couldn't find any option on github.
  - And you want to refer another person only to the folder? << yes
    - it can be OK to start with few related scripts collected in one repository and then I sometimes browse the project on GitHub and send a link to the directory, example: https://github.com/bast/cicero/tree/master/cicero/templates (link to subfolder)
  - For small snippets I use Gists (they are version-tracked, too): https://gist.github.com/bast << Thanks 
    - nice thing about gists is that you can also have private gists only for you


#### Dependencies

- What if you use some other language then python?
    - Most languages have a similar concept (at least most newer languages)
        - We do most of our work in C++
          - in this case there is conan.io (but I haven't used it yet), alternative is Conda (environment.yml), but it can also help to document dependencies in the documentation
- What is a superfund site? I
    - USA concept of "environmental disaster sites so bad, they get taken over by the federal government to manage clean-up"
- Is it possible to share the code with all dependencies (i.e. environment)?
  - Yes, containers are a solution that packages also the dependencies with the code
- What is the standard way of making requirements files if not all sofware is possible to install through conda, so you have to mix conda install and pip install. Do you have both a requriements.txt and and environemnt.yml file?
    - environment.yml can also include a "pip" section (if you install some stuff with pip, it appears in that section).  It mostly works but can quickly become difficult to manage!
    - and as far as I know, Conda can also deal with requirements.txt, right? but the above answer seems better, I did not know, thanks!
- What is `bioconda` (a Conda channel)?
  - A conda channel for bioinformatic related software libraries 
  - One can collect packages in "channels" - basically, a way for a person/organization to release their own packages which can overlap with others
  - You can also start your own channel
- remark on conda dependencies: it is not encouraged to manually install one or more packages in an environment (which is usually created from an environment file) and then share the updated dependency list through $conda env export 
    - +1.  It gets difficult to distinguish the minimum requirements needed to recreate the full list.  I've spent too long separating these big lists down to the minimum requirements...


#### Containers

- I mostly use Docker, but currently I need to submit work to an HPC which only accepts Singularity. I know I can convert a Docker image to a Singularity one, but I wonder if there is an easy way to convert a Dockerfile recipe to a Singularity recipe.
    - I'm also interested in learning how to do that, I only know that it is possible. I searched a bit more on the web and there are a number of resouces but I haven't tried these yet.
    - I've heard some way to directly convert image → image, and I think I've done it once but I don't remember details.
    - Converting the images is possible. But I need to have a large CFD package compiled in it, which means my Docker image is large in the first place. That's why I am planning to just have it done in Singularity from the beginning (then I can do it directly in the Swedish NSC).
      - indeed several HPC centers are moving towards Singularity and I would be happy to learn from your example once you get it working.
      - Sure! I will try converting the Dockerfile first. In the worst case, the syntax for Singularity recipes seems relatively simple.
      - this could help https://github.com/hpcng/singularity/issues/1537
      	http://singularity.lbl.gov/archive/docs/v2-3/docs-docker

#### Recording computational steps

- How powerful is Snakemake? Can it handle complex workflows? Thanks for showing me this tool. I could imagine it is really helpful to control data analysis steps with variable inputs etc.
   - complex in terms of many steps with various dependencies? I think snakemake can be a good tool for this. it is not the only workflow orchestration tool, there are many, but it can be a good starting point.
     - complex: a workflow with lots of sub-steps. It looks like Snakemake is a cooking recipe where I can process many files with the same instructions. So far I used only scripts and had to modify manual the input. Seems really useful.
   - snakemake allows you to run programs as part of its setup. If you structure your code to run as components it can be very versatile.
- Does snakemake from PyPI work as well?
  - yes it should work, this is how I use it
- is there a difference in the way snakemake and make figure out already existing dependencies?
  - no, make and snakemake both use the timestamps of files to figure out which targets need to be recreated if some dependencies are updated
  - if this question is about how does (snake)make know what depends on what? if yes, then this is what we need to tell (snake)make in the Snakefile by expressing dependencies. but in contrast to scripts we do not need to script the order of executions, only declare what depends on what and Snakemake will figure out the order of execution and also can run steps in parallel which are independent of each other. 
- Does Snakemake work together with Git somehow?
  - it doesn't interface with git or use Git directly. But you could include Git commands in a Snakemake rule
    - E.g. run git at the end to keep track of the changes?
      - well, maybe you shouldn't track the generated files with Git. Normally you only want to Git-track source files, data files and key results. But running git pull or git clone might make sense in a snakemake workflow (and e.g. check out specific versions/tags)  
      - (see last point below)
- it is good to track Snakefile as part of the project as part of the Git repository but perhaps the question was about something else?
    - But can this be done automatically? Snakemake seems to be really fast and can change a lot of things at the same time.
      - You could automatize a workflow using GitHub actions or Travis CI or GitLab CI (or similar services) and let it produce something upon each Git push or accepted pull request or release.
  - I think normally you would: track Snakefile with git, along with the rest of stuff.  .gitignore any automatically-generated or modified outputs.  The stuff snakemake modifies or changes, you assume you can automatically regenerate, so you don't track separately (except in special cases)

- I guess it becomes important to manage your environment/requirements when doing releases/tags on github?
  - it is good to make these files part of the repository, also for those who clone/download them perhaps years later and need to recreate the same environment
  - Yes!

### Social coding

#### Initial activity

Reasons for sharing:
- get input from other people (improvements, debugging)
- other innovative uses of code and data
- validating your results by help for others
- Feedback from others. Develop code so it applies in a broader context
- Develop your own coding skills
- 3rd party contributions can significantly boost your project 
- more eyes gives higher quality both in use and for finding code errors
- it motivates innovation across fields and practices
- You can decide if code is private/secret if there are things to not share. At least it is backed up under version control
- It as an additional way to review your methods. Description in methods in a paper is sometimes limited, and reading the code may reveal additional aspects of the work.
- more citations when published
- good for you CV
- it allows you to keep access to your developments after your job changes

Reasons for not sharing:
- Code not in a stage where it can be shared
- "one person does all", others just observe and don't contribute
- research can be competitive, get most out our software
- patenting is impossible after publishing (fx. algorithms)
- Don't want to share unstable code
- Industry standard for not publishing code. Secrecy
- wanting to get the most out of data/algorithms/code before someone else
- Confidentiality agreements
- time requirements for reviewing pull requests
- don't want to give up competitive edge
- "ashamed" that the code is not up to "standard"
- code can be wrongly used and produce wrong results which get associate with the code
- patent issues with certain markets (fx. US vs EU software patentability)
- I see an interesting pattern above: both "it's too messy and others can't use it" and "it's too valuable to me, others will get an unfair advantage".  I wonder how many people think both at the same time...
  - indeed very interesting combination

Why is software treated differently?
- regarded as a tool
- less respect for developing software
- innovative pressure is much higher, software is easy to improve upon
- remixability. same algorithm can be used for many purposes and applications
- Citing the software not so established as citing a publication
- people are afraid of others finding errors
- You invest a lot of effort and time developing a software. If you share it, people can 
- it's a bit like a lab journal, many people would be hesitant to share that one
- different standards set by journals



#### Other questions/comments

-  given enough eyeballs all bugs are shallow
  - it is a really nice moment to get a bugfix from somebody else you have never met 
- Suggestion for the future: If a PI give such an answer regarding the software and the data, his paper should be retracted.
    - which one(s) of them? 
- Can you tell more about limits institutions might set on open sourcing code?
    - good to check with the institution since it depends but often they don't know either
    - there is a difference between ownership (copyright) and license
    - typically ownership is with the employer (exception: Sweden?) but academic institutions typically encourage open source but it can put you into a conflict since only copyright holder can change license so it can be helpful if the university has a policy on this
    - I've noticed a great disconnect at mine: admin is constantly saying "you should be more open!", but not making it clear or easy to do it.  I had to struggle to get a note in our "open source policy" saying you are allowed to open source it...
- I am curious: When you started your positions, have you been informed to whom belongs the code you would develop? 
  - I haven't, it was never discussed and for many years it was not clear to me.
  - ownership can be a problem when you go to a competing group later or once money starts to be involved
  - in Finland universities, ownership depends on the type of funding you have.  The ministry puts pressure on universities to be more open, so you should be able to find some sort of internal support to make a policy to open things.
  - I found out later: The code is mine, the data belongs to the university. 
- If a project is not "active" and many pull requests open, this does not have to mean the library is not useful. Sometimes the author simply has no time to process the issues and pull requests and would be happy if somebody else contributed not only questions but also answers. Often questions start flowing in years after the project/funding has ended.
    - Good point, perhaps you could offer help organizing it?  What else you could do is start working on improving in yoru own fork, but then that divides the community.
- What is an attribution?
  - basically make somehow clear where the code/idea comes from and not relabeling it as own idea (author, source URL)
  - to refer to where the code has been copied from, who was the original authorj, under which license the code is shared, and possibly what modifications were made
  - 
- Regarding attribution, how is it a good way to do it?
  - not claiming this is perfect but this is what I did: https://github.com/bast/polygons/blob/master/src/tree.rs#L387-L395
  - https://wiki.creativecommons.org/wiki/best_practices_for_attribution

- What if we use codes from different types of licenses? How can we share our code?
  - check whether licenses are compatible: https://en.wikipedia.org/wiki/License_compatibility
  - this is also why it is good to take a standard license and not invent your own, otherwise compatibility may not be clear
  - you can include permissive in share-alike and strong copyleft but the other way around would be more problematic

- Can we change license later?
  - you can as copyright holder
  - mind that as project grows, all contributors may be the copyright holders so you may need to get agreement from everybody who has contributed so it is easy to set and change early in the project, it can be more difficult later
  - as an anecdote I have spent one year moving a project to another license because we needed to get agreement from all past contributors
  - But, people who use it under the old license can still do so!   So it's not retroactive changes.
    - Right, I cannot change it for already released versions. If I give you a code under LGPL, I cannot later take it away from you but I can decide to release future versions under a different license.
    - Make sure you use a CLA (contributor license agreement) if multiple ppl work on the code
      - but CLAs might also "scare away" contributors so I have been hesitating making things too formal for small projects but for larger projects it may be needed. 

- Are we giving up copyright when we use an open source license?
    - You still "own" copyright and can change later.  see above for considerations, though.
    
- What other tools, apps are there to facilitate social coding or even collaborative work?
  - great question - growing communities is not easy. One can use a chat but it's often one more chat tool. Many projects use Gitter to discuss, GitHub will soon provide "discussions" for projects.
  - contributing guide can help but it often takes time to get people involved
  - maybe labeling issues as "good first issues"
- For attribution. Everytime we use some code that has an attribution clause in the license, should we include an attribute in our own source code? For instance each library loaded in a script, does it require its own attribution?
  - I would attribute it in the source code but if it is a significant contribution, then also credit it in the documentation and possibly also in the recommended citation or metadata (https://citation-file-format.github.io/)


### Feedback on day 1

(feedback on certain episodes can also be added to their sections above)
- The HackMD is really nice!
    - the best thing about it is that it remains accessible under the current url.
    - we will later move (anonymized) questions and answers to https://coderefinery.github.io/2020-05-18-online/#questions-answers-and-feedback
- I did like diversity in subjects. It was slow in some parts for me but quite interesting. Thank you all!
- Many useful details, it's great. thanks!
- Snakemake archive my new fav!
- Maybe a bit more specifics about license and less general would be nice
- i really like all subjects and versions but for a completely newcomer to snakemake and similar (and to virtual environments in one sense) it went a bit fast sometimes. maybe i had lacking pre-knowledge but a bit fast. however despite the speed i really like the content!
- I liked the flow of this workshop, with good interation during presentations and also on the group discussions.
- Nice workshop again. Snakemake looks really helpful. I wish you could dedicate a whole session to it. 
- I think the workshop needs to be stretched timewise more. 3 hours don't seem to be enough for the online version. Maybe everthing is slower? Some things were rushed due to the time restriction.
- Longer breaks please
- Timer on screen was a good idea during breaks.



### Documentation lesson

#### Is project documentation important? Why?

- it is important to me. we collaborate a lot in our group interchanging knowledge and scripts and code snippets and apart from having to document as a part  of university it is important so we can track and understand. it has happened that code have been left to another person with insufficient comments or explanations and then it is barely a difference in time between getting a script and reinventing the wheel and making a new one sometimes
- Very. If for nothing else to be able to understand my own code later on.
- Yes it is important for sure. Either for our referencing or other to be able to use.
- Very important. It is very easy to forget what have you done and why. It also makes it easier for people to contribute or use your data/code.
- It allows users and developers to understand the code. It makes it easier for corrections and improvements to be implemented by others. It is also important for future use by the developer, as even our own code can seem confusing after some time without seeing it.
- Provide help/insight for the future self
- very important 
- Yes, it is very important for being able to reproduce even your own code or your collegues. 


#### How can you motivate your colleagues to contribute to the documentation?

- Code becomes re-usable for others, easier to maintain. 
- Maybe also a chance to find errors better.
- collaboration 
- collaboration
- Having a standard practice for people to follow and to keep up with.

#### How would you describe a useful documentation?

- Useful, when it provide the necessary details, a clear description. Explains what the programm does, what are the input variables, what are the output variables.
- reproducibility of the results 
- Something that has a low threshold to start, so it isn't as easy to skip it.
- Reproducable.
- When anyone can understand what is the aim of the program, what the code does, what is the input and output and an example.
- It should be simple and describe well how the code works. It should also present reasons for some important coding choices by the developers.
- Has examples
- Upto date!

#### Let us create a wishlist for how we would like documentation to be.

- Easy to follow. Clear. Incldude simple example of how to use.


#### Documentation questions

- How to document small scripts, and collections of such? There are a lot of these small scirpts that doesn't belong to a speicific project as such.
  - a README file can go a long way. Comments in the source code are also valuable, but often not enough, especially not for users who might not read code
  - We will see later how to document larger projects which might need something more than a README
    - do you store the scripts in a common folder? in the same repo?
      - A common folder, outside the project. A set of tools for everyone to use
        - Maybe a README in the same folder with a list of the scripts and a how-to-use description of each. Don't have a better solution from the top of my head
        
- If you click for example on Feature A in the menu on the left, Feature B disappears from the menu, and you have to go back to see it again. Can you configure this somehow so it always shows?
  - this is how I solve it:
    - result: https://runtest.readthedocs.io/
    - source:
      - index.rst: https://raw.githubusercontent.com/bast/runtest/master/doc/index.rst
      - doc folder: https://github.com/bast/runtest/tree/master/doc
- How does adding jupyter files work with sphinx? Compared to just putting it in GitHub?
  - You can add jupyter files but it will need nbsphinx extension to be installed. 
  - GitHub has probably required extensions in place.

- I could figure out where to put Level 1, level 2. I got a warning and it does not appear. Edit: I figured it out. It seems indentation is important.
  - yes indendation is crucial! 
  
- Could you maybe show how to include the image, please?
  - did you try this: 
    `.. image:: image.png` ?
      - I repeated it and now it works. Thank you.

- Does this work as smoothly with bitbucket also? 
    - yes, if you select "Import manually" you can enter the URL of any repository (github, gitlab, bitbucket...). And even repos in other version control systems, e.g. subversion
- And can you use readthedocs if your repo is private but you want the documentation to be public?
  - ReadTheDocs free service can only serve public repositories.
  - You can use paid ReadTheDocs or
  - You can run your own sphinx server or
  - You use GitHub actions or GitLab CI to run Sphinx upon each push/merge and serve the generated HTML on GitHub/GitLab pages
  - I would keep the master branch public (this is the "published" code), serve public doc from it, and have side-branches for unpublished code where documentation can either be generated locally or on a private server
- What is the trade-off between hosting the site on Read The Docs and using Github.io? 
  - also answered below. on RTD you can very easily create documentation for several branches/tags at the same time but on github.io typically only one branch/version
  - but you could run your own Sphinx server also that builds Git repos for you
- Could you configure sphinx-quickstart to build a custom starter setup?
  - you can add pre-processing and other steps into the conf.py which gets run on each build 

- In generated html by read the docs there are ads. Is this because of code in docs or it is something by readthedoc and we can not remove it?
  - readthedocs.org has only "ethical ads" and kindly asks users to not block them since they offer a free solution.  (It's part of the RTD custom theme as part of their serivce, not a sphinx feature)
  - you can make sphinx part of GitHub Actions step (or GitLab CI step) and deploy the generated HTML to GitHub/GitLab/Bitbucket pages and then you are in full control but maybe can only serve one version at the time


### Jupyter notebooks lesson

- Why don't we use Jupyter instead of readthedoc html files. Github alread shows jupyter files like an html in github.
  - Jupyter works really well for "linear" projects, scripts and libraries and if this fits well your project, then it can be a better solution than RTD
  - It works well for languages and projects which can be scripted and have a progression of steps
  - But some projects don't fit too well into this but it is a matter of taste also
  - Just using Jupyter leads to a "big mess of files", sphinx provides structure.  you can use both: there's a way to insert jupyter notebooks as pages within a sphinx project, so you have the best of both.

- This is sounds very simular to Mathematica
  - Very similar indeed. Advantage: Jupyter is open and free (both in money and legal terms)

- How can we add the launch binder button?
  - Visit https://mybinder.org/ and insert there the URL of your Jupyter project
  - More detailed steps: https://coderefinery.github.io/jupyter/06-sharing/#exercise-making-your-notebooks-reproducible-by-anyone-via-binder
  - If your repo contains a `requirements.txt`, Binder will use that to create the environment

- RStudio vs Jupyter
  - Similar idea and possibilities and if you are familiar with RStudio, probably no reason to switch
  - You can also deploy RStudio to Binder. Example: https://github.com/bast/rstudio-on-binder


- What are the advantages of Julia? 
  - Compared to Matlab? It has similar syntax as matlab but it is free and open
  - Type safety
  - More high performance than Python or Matlab
      - In comparison to Python. Could you elaborate the higher performance, please?
        - Python has a huge ecosystem of libraries and packages, Julia is relatively new but also growing community and ecosystem
        - It is possible to write Julia code which is faster than traditional interpreted languages like Python since it compiles the code (just in time). I have personally too little Julia experience and if I need to speed up Python code I rewrite part of it in C++ or Rust.
      - Could I use python libaries in Julia?
        - I hear it has very good interoperability with Python but I have no own experience with this.
- I use Rstudio as a literate programming tool, then I can produce HTML or PDF withknitr package. What would be the pros/cons to use jupyter instead?
  - RStudio is very good tool to  work with R, so no need to change.
  - similar question also above
- I followed your instruction to install the extensions, but they don't appear in my jupyterlab.
  - For me I had to stop and restart JupyterLab again to have them available
   - Thank you. I started it freshly, but nothing. I will investigate. 
- Why would I use jupyter instead of Mathematica? (we have a site licence...)
  - Because after students/postdocs leave academia they are often surprised that they lose the license and get locked out of their tools. Often this is available to universities but can get quite expensive outside of academia.
  - I have spent some time giving support to research groups porting code from Matlab (different language but same potential problem) to Python because it got too expensive for them but rewriting code is expensive, too.

- I always find it bit annoying not being able to move back and forth with folders in jupyter notebooks or jupyter lab. Any solutions here other than command line operations? 
  - It seems one cannot "escape" out of the root folder where Jupyter was started from.
      - Yeah, that's a "feature".  since I want to use it as IDE-like thing, I always start from home directory and navigate to where is needed.

- Can I use variable values within a Markdown block in a notebook??
  - Just browsed a bit, there are extensions for it but they don't seem to be supported anymore so I am unsure whether this is possible.

- Could I ask after the workshop for help with the extensions, please? My jupyter-lab opens now with an error message all the time.
  - We will stay around and can then debug it after the session by screensharing. 
  - https://github.com/coderefinery/jupyter/issues/62
  - `jupyter labextension install @jupyter-widgets/jupyterlab-manager`


- Is it possible to execute with Snakemake jupyter notebooks and provide maybe inputs?
  - Snakemake would then execute jupyter in command line mode and generate outputs for other steps of the workflow?

#### Git extension

- contents of $HOME/.jupyter/jupyter_notebook_config.json

```
{
  "NotebookApp": {
    "nbserver_extensions": {
      "jupyterlab_git": true,
      "nbdime": true
    }
  }
  }
```

### Feedback

What worked well and what should we change/improve?

- Maybe it would be nice to include how to test for the github/widgets for jupyter in the information that is given beforehand so we can use the given time to do the actual exercises. That or having longer sections for jupyter. 



### Automated testing lesson

#### Questions

- What about testing depenencies?
    - Do you mean, testing that it works with different versions?
        - Most testing platforms (like travis, as we'll see later) can do multiple runs so you can run a matrix of different dependency versions.  So, e.g., I test with current numpy, numpy from 5 years ago, etc.
    - Maybe what is meant is testing the library that I am depending on. If yes, and if this is a much used library, we can hope that they do that already but it is still good to test the combination, that the whole thing works from input to output, passing through the libraries that I use.
    - In compiled projects (CMake) you can configure things so that when you run the test set for the "parent project", it also runs the test sets of the included libraries.
- What are the parameters to be considered while testing ?
  - For unit tests: considering the various possible inputs and checking the outputs of the function. It may not be possible or practical to test all possible inputs.
  - Often we test input parameters in some reasonable range.
  - But in can also be valuable to test unreasonable parameters, and making sure that the code fails in the expected way
    - Good point. Also recent failures/bugs can be good inspirations for extending the test set.

- How much time should be spent on testing? I noticed I could easily spent the double amount of time of writing tests than the actual code? At some point I got very defensive and checked for each input.
  - It is a balance, not only about spending time but also creating more code which may help or hinder refactoring (rewriting/optimizing). I would not try to test everything but often I do start with tests when I know what behavior I want but don't know yet how to do it. Also I would test the non-trivial code, code that recently broke, and I would start with an end-to-end test where I make sure that selected use cases produce the results that I expect them to.
  - I could easily spend double the time debugging compared to writing, so if I can get around to it, spending that time writing tests is better spent.  In practice I do what is above, test what I can do easily, and expand later while debugging.

- What does refactoring means?
  - Rewriting/changing the code, so that it has the same effect but operates differently.  With tests, not so bad, without: you get all the same bugs again!

- Is there a website with test examples? 
- 
  - there are at least pages with excellent overviews and examples for individual testing frameworks:
    - https://docs.python-guide.org/writing/tests/
    - https://realpython.com/python-testing/ 

- where do I put my tests?
  - typically you make a `tests/` directory, but also very convenient (at least initially) to keep the tests close to the code it tests

- Is there any program that have github integrated testing that works on private repos? Travis only works for public ones, if you don't pay
  - GitHub actions or GitLab CI can be run on own test runners


### Modular code development session

Reload your browser tab, material is here: https://github.com/coderefinery/modular-type-along


#### 1. What does "modular code development" mean for you?

- easier developement
- Separation of concerns
- Functions. Brake down the tasks into  smaller code blocks.
- Independent blocks/functions
- Smaller sections, manageable 
- DRY (don't repeat yourself) code
- reusable code
- Writing code that can be used multiple times
- library developemnt
- for me it mostly means that I can copy-paste/ reuse a function/module to a different project or a different place, and it still works


#### 2. What best practices can you recommend to arrive at well structured, modular code in your favourite programming language?

- Well documented on the requirements of a module
- No global state
- No singletons 


#### 3. What would you recommend your colleague who starts in the same programming language?

- There is no "temporary code". Don't treat anything as such.

#### 4. What do you know now that you wish somebody told you earlier?
- It is an iterative process that requires experience. I don't know how many times I re-wrote the code.
- How can I improve my coding skills, how to improve for modular programming?


#### Hints and questions during the type-along

 - Decide license, so you can decide what type of code you can copy and which libraries you may use.

- the plt commands use global state... 
- Include short comments when you introduce new lines (to include lables etc..)
- avoid hard coded filenames, pass in as argments

- write a function for estimating the mean and a function for the plot
    - Loop over the number of measurments


- write a function

- What about only reading the file once, with all the rows, and plotting a certain range each time?
    - Perhaps just read in the maximum number needed? Make the range an array and get the maximum number
        - Makes sense! :)

-  seperation of concerns (reading data, calc mean, plotting)

- .gitgnore file
- Test data before plotting, is the file havving same number of columns  in all raws

- in plot_data: num_measurements should be removed, add filename instead as an argument. In the same way x and y labels and change temperature to a more general name

- plot_data() should also take the mean as in input...
    - You could actually call the mean function inside of plot_data()

- why does that work? scoping is strange in python,
    - that is horrible
    - In this case, `mean` and so on are defined in the global scope.  A reason to avoid global scope for things, you get these subtle bugs!  (yes, I agree it's bad)
        - so if you do a def main:  and then if `__name__ == __main__: main()` thing then that can not happen?
        - right, it won't happen.  I just tested.

- would you write- a class instead?
    - That would provide even more encapsulation, which could be good.  it's most useful when you may need to keep the code close to data and do subclassing to make slightly different versions.

- What does the instructor use for auto-fill in his terminal? It gave a suggestion when writing commands.
    - The `fish` shell, has more features for interactive work

- you could also add the `if __name_ == '__main__'` so you can impot the functions to other scripts also, or run stand alone
    - Yes, it should eventually evolve that way (like it just did)

- should you not ensure your data file has the right format?
    - Would be a good idea, but probably not enough time to do it now.  assertions/defensive programming from the last episode fits here.

- Sorry for this strange question. But pytest targets automatically the function that beginns with  test_ ?
    - yes, in python you can ask a source file for all the functions in it and their names and then run all the ones that start with some pattern like test_

- What is the definition of "side effects"?
  - when a module or function modifies data outside which can affect other parts of the code 

- What is pure function?
    - same input should always give the same output
    - No side effects (doesn't modify any other variables), and depends only on the arguments (so none of this "using global variables" problem like we saw)
    - depending on the context sometime you would still allow side effect as long as they are not observable. which is very useful for memoization

    - Yes, my question would have been how to use this with SnakeMake.

- [I reverted from the old versions (at xx:35), we lost the last questions, please ask again]
- What would your workflow be to loop now?
    - Either write a script, or something like Snakemake that is being descibed now

- How do you make sure that you can find these functions in a year? Document somewhere?
  - These days by sharing (GitHub/GitLab) almost everything publicly with others and with my future self.
  - Gists for small code snippets.

- Unrelated to the modular code session. Is it possible to do a parametric study using snakemake+script? What would be a suggested workflow?
  - Parametric study means looping over a parameter range and run some step(s) for each of these? Yes!
    - I would probably write a shell script if the whole study is quick (minutes). If it takes hours or days and many steps, then I would go for a workflow and loop inside the workflow.


### Feedback

What worked well but also what we should change or improve.

- Great workshop! Maybe for the online version would be nice to encourage participants to have their videos on. It's kinda nice to see other people.
- Appreciate all your efforts
- Modular code development was awesome! 
- It was a really useful workshop! I can't wait to implement all these in my daily work. Last day was very fun with the type along. I think a bit longer session would be good to be able to do all exercises. I think the lectures and exercises wer great. Helpers were great. I liked it a lot. Thank you!  

- I didn't manage to find a conda `requirements.txt` file for creating the environment for the whole workshop (or for each day)