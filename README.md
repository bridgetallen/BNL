# BNL

# Viral Analysis End-to-End

Metagenomic dataset from Global Ocean Viromes 

Step 1 - Import files as SRA
Step 2 - Use FastQC to check quality of data
Step 3 - Quality control - use trimmomatic to trim data
Step 4 - Post QC Read assessment using FastQC
Step 5 - Use MetaSPAdes to assemble
Step 6- contigs input_assembly_refs
min_contig_lengthMin Contig Length
output_nameOutput name
Step 6- Use Virsorter to identify viral genomes 
Step 7 - potentially viral Use Virsorter
Step 8 - use vConTACT2 to classify sequences
Step 9 - Use Prokka for predicting genes
Step 10 - vConTACT2 again

# PEP 20 - The Zen of Python

PEP 8
- code layout
- imports
- naming conventions
- spacing
- comments
- docstrings
- comparisons
- code should be readable and consistent

# RNA-seq Primer

Step 1 - Upload Genome data
Step 2 - Import single end reads from the internet (Parameters
download_typeURL Type
sequencing_techSequencing Technology
fwd_file_urlFASTA/FASTQ File URL
single_genomeSingle Genome
nameReads Object Name)
Step 3 - create a sample set for experimental data using "Library Type", "Domain", "RNA-seq Sample and Condition Labels," and provide the "RNA-seq Sample Set
Step 4 - FastQC (input_file_refRead Library/RNA-seq Sample Set:)
Step 5 - Align Reads using HISAT2 
Step 6- Assemble Transcripts using StringTie
Step 7 - Create Average Expression Matrix (expression_matrix_refExpression Matrix: KBaseFeatureValues.ExpressionMatrix)
output_suffixAverage Expression Matrix Name Suffix
Step 8 - Identify Differential Expression using DESeq2
Step 9 - Create Feature Set and Filtered Differential Expression Matrix
Step 10 -  Functional enrichment of differential expressed featureset


Client-Server Architecture 

common verbs:

get "read"
post "create"
put "update"
delete "delete"

# KBase SDK

- when you run an app in a narrative, it runs in a docker container on KBase

User Input - parameters are listed as references, think of these as URL's to download the files, elements can be customized to accept different kinds of data

App Code and Data Management - input is converted to a python dictionary, then algorithms are run

Output and Reporting - KBase report is generated 

Command-line Interface - called kb-sdk and makes it easy to initiliaze, validate, compile, and test your app

Docker - apps run inside docker images and the interface runs within a container

Composing apps - when you install and run another app within yyours the other app runs on it's own  seperate docker container. also tracked seperately from python dependancies 

KBase Types and Parameters - config files use used for parameters and output 

Working with files and data (Scratch and the Workspace) - scrath is ephemeal so any files in this directory are gone when your app stops running. workspace use if you want the user to see in the narrative.  a dataset in the workplace is referred to as an object 

The Catalog - registry of the apps. three catalogs for testing purposes: dev, beta, and release. dev = prototype beta = requires testing, release = visible to normal kbase users

Publishing 

every vector space has a basis

# dowloading kbase kb-sdk

Step 1: Check docker is installed correcly and that it can pull kbase 

:~/suli/kb_sdk$ docker pull kbase/kb-sdk

Step 2: make bin for directory you want to put kbase in, then run genscript and chmod

:~/suli/kb_sdk$ mkdir ~/suli/kb_sdk/bin
:~/suli/kb_sdk$ docker run kbase/kb-sdk genscript > ~/suli/kb_sdk/bin/kb-sdk
:~/suli/kb_sdk$ chmod +x ~/suli/kb_sdk/bin/kb-sdk

Step 3: add to your path

:~/suli/kb_sdk$ echo 'export PATH="$HOME/suli/kb_sdk/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

Step 4: Check it worked 

~/suli/kb_sdk$ kb-sdk
:~/suli/kb_sdk$ kb-sdk version

Step 5: initialize with github user and your module name 

~/suli/kb_sdk$ kb-sdk init --language python --user bridgetallen bridgetallenContigFilterHelloWorld

:~/suli/kb_sdk$ cd bridgetallenContigFilterHelloWorld
make

:~/suli/kb_sdk/bridgetallenContigFilterHelloWorld$ cd bridgetallenContigFilterHelloWorld  # only needed if not already in the correct location
git init
git add .
git commit -m 'Initial commit'

:~/suli/kb_sdk/bridgetallenContigFilterHelloWorld$ git push -u origin master
Username for 'https://github.com': bridgetallen
Password for 'https://bridgetallen@github.com':


:~/suli/kb_sdk/bridgetallenContigFilterHelloWorld$ cd ~/suli/kb_sdk/bridgetallenContigFilterHelloWorld

:~/suli/kb_sdk/bridgetallenContigFilterHelloWorld$ kb-sdk test

# Arabidopsis RNA-seq Analysis Tutorial Questions 

1. If FastQC says your reads are no good, how is HISAT2 still able to run and align the reads
2. What does a normalized distribution say about the the gene expression?
3. It says that my expression matrix was successful, but I don't see useful information in the details.
4. Since we know that Arabidopsis is normal, if we saw an unusual dot on the PCA plot, would it be of interest or a known outlier?
5. What are the most common and most uncommon apps used in this analysis?

# HTTP Project 

cloning vs. creating a new repository 

Action	GitHub UI	Command Line
Create new repo	“+” → New repository	mkdir → git init → git remote add
Clone existing repo	Click “Code” → Copy HTTPS link	git clone https://...


Preliminary steps: 

1. Make a new repository on the github browser

In Ubuntu:

2.  Go to your main project directory (ex. suli folder),then create a new module for the project (e.g. flask-http-assignment). Make sure to stay in this directory at all times during the project.

3. Create and/or activate virtual environment.

4. pip install flask. 

5. create app.py.

6. in the vim, Built a Flask Server with Three Endpoints (see app.py for code).

GET /
Returns a plain "Hello World!" message.

POST /echo
Accepts JSON in the request body and returns it back in the response (an echo server).

GET /pokemon/<name>
Acts as a proxy to the PokeAPI, returning real-time Pokémon data for any name passed in the URL (e.g., /pokemon/eevee).

7. esc, :wq, enter to leave the vim.

8. run your server with python app.py.

9. for the first end point: open http link (given in the output for python app.py) and see hello world.

10. for the second end point: open a new ubuntu tab and use the curl command and http link plus "/echo \" to enter the content type and a message to see the echo reflected in the output.

11. for the third end point: manually type in any pokemon to the end of the http link to see the output example: add "/pikachu".

12. initilize git, add your files, commit, specify branch, add origin (URL from browser), push (anytime you need to make changes to the code in vim, you must stage changes, commit them, and push them).

13. Check github to ensure your changes are saved.

Flask PokeAPI Proxy

HTTP Server and Client

API - Application Programming Interface (example - weather app)

BASH Variables 

your_kbase_username=bridgetallen
username=${bridgetallen}
module_name=ContigFilter


git remote add origin https://github.com/bridgetallen/HTTP-Assignment-.git
git branch -M main
git push -u origin main

Abstract Data Types (ADT)

definition- math model for data types defines by its behavior from the pov of a user of the data (specifically in terms of possible values, posible operations of this data types, and the bahvior of these operations)

ADT vs. Data structure 

- ADT is a conceptual interface
- data strcuture - actual implementation (e.g. stack implemented with an array or linked list)
- the key is abstraction - hide how data is stored, focus on what operations do 

formal specification
- described by interface and operations (incliding pre-conditions and post-conditions)
- contraints define behavior (e.g. for a stack) push(x) then pop(x) must return x

Operational semantics 
- ADT's can be mutable, where state changed over time 
- E.G. operations beyond basics create(), empty(), hash(),

Multiple instances & Aliasing 
- ADT's must support multiple instances independantly 
-changes to one ADT pbject should not affect another - important for corectness

Complexity Considerations 
- ADT's often specify time/space constraints for operations, even though implementations differ. 
- e.g. a stac ADT remains the same conceptually whether backed by an array or a list 

Common ADT's 
- collections- list, set, multiset, map 
- linear structures
- hirearchial structures 
- priority structures - 


Project Applications 

- Build a Web API from scratch 

- API's power most modern apps
- expereince building and using a flask (a lightweight web framework)
-learn how to define endpoints, handle HTTP methods, and return structured data using JSON

- work with JSON and HTTP Requests

- JSON is the standard data format for web and mobile communication
- you learn how to send and receive data using curl, which mimics how real apps communicate with servers 

- Use a proxy pattern

- your pokemon acts as a proxy 
- it receives a user requests, forwards it to an external API, and returns the result 
-this is how apps like the weather app, stock trackers, and flight search tools work behind the scenes 

- understand modular, testable code

- each route has a clear single responsibility
- you can easily test each rpute using tools like curl or postman 

- version control and collaboration

- git workflows
- collaborating on open source or team projects 

- real life applications 

- get / hello world - health check to confir, the server is running (used in production)
- post /echo - forms, chat apps, or APIs that accept and valicate user input 
- GET /pokemon/<name> - search finctions or recommendation systems using external APIs 
-  JSON parsing - used in apps like slack, instagram, and mobile weather apps 
- flask + rest API - used in microservices, data dashboards, machine learning model deployment
- proxy endpoints - used in bioinformatics tooks, financial apps, and news aggregators to fetch external data and format it internally 

# Different ways to make matrice multiplication functions in the command line 

Easiest way: download numpy in the current directory, enter a vim, paste matrix A and B, exit vim, run script with python3 matrix_mult.py

How to hook it up to the HTTP assignment 

use the post method and a multiplication route, then run a curl command making sure app.py is running 

alternative (not using):

- bash script: #!/bin/bash, define matrix A and then B, check dimension compatibility, initialize result matrix C, print result 
- not scalable for large matrices

Proof for checkerboard equation:

- even with an even number of squares on the checker board, you're unable to cover all of the squares with dominos because with the top right corner and bottom left corner missing, it creates an irregular matrix. 

- while the board doesnt have to be a perfect square, the blocks need to be removed in sets of 2.4,6 etc

6/11

recursive- the function calls itself in order to solve a problem 

Exponentiation with matrices

| Feature       | Plain python         | NumPy
|---------------------------------------------
|               |
|Speed          | slower
|Syntax         | verbose (manual loops)
|Memory         |
|Math functions |
|
|
|
|
|
|
|

Github Actions 

- Github actions is a CI/CD (Continuous integration / continuous deployment )
 platfform built into github. it automates tasks like:

 - running test when you push code
 - building and deploying apps
 - checking code formatting or linting 
 - triggering workflows on pull requests, issues, or scheduled items 

 github actions = repeatable tasks done automatically every time you update your code 

 how does it work?

 - you create workflows using YAML files stored in: .github/workflows/
 
 Each workflow is made up of:

 - events - what triggers the workflow (e.g. push, pull_requests)
 - jobs- tasks to run (e.g. run tests, deploy code)
 - steps- individual commands (install dependencies, run a script)
 - runners- the virtual machine that runs your jobs (linux, windows, macOS)

common use cases

task

run tests                   every push triggers a test suite
build projects              compile a react app, flask app, etc.
lint/code/style             auto-check for PEP8, BLACK, ESLint, etc.
deploy app                  Auto-deploy to Keroku, AWS, or Github pages
scheduled tasks             run data sync scripts nightly

- workflows- configurable automated process that runs one or more jobs. workflows are defined using YAML files and can be triggered by events in the repository, manually or on a schedule. These workflows are stored in the .github/workflows directory of the repo

events- are specific activities in a repo that trigger workflow runs. examples include creating a pull request, opening an issue, or pushing a commit . workflows can also be triggered on a schedule or manually.

jobs- set of steps ecexuted on the same runner. each step can be a shell script or an action. jobs can run sequentially or in parellel, they can share data between steps. jobs can also have depencies on other jobs.

actions- custom application for the github actions platform that performs a complex but freuently repeated task. actions help reduce repetitive code in workflow files. they can be used to pull a git repo, set up a built environment, or cinfigure cloud provider credentials

runners- servers that execute workflows. github provides ubuntu linux, microsoft windows, and macOS runners, each workflow rin takes place on a new, freshly provided vim. users can also host their own runners if they need a different operating system or specific hardware setup. 

Fibonacci Numbers:

The Fibonacci sequence is a series of numbers wheere each number is the sum of the two preceding ones:

starts like this: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...

- the ratio of consecutive fibonacci numbers gets closer and closer to the golden ratio (1.61803...)

Recursion vs. Induction

recursion is when a function calls itself to solve a problem. it works by

- breaking a problem into smaller subproblems
- solving the base case (the simplest form )
- letting the function call itself with a smaller output

recursion is common in algorithms (searching, sorting, tree travlersal ) and math definitions 

indiction is a proff technique used in math to prove statements that are true for all natural numbers. it has two steps 

1. base case: prove the statement is true for the first value (usually n=0 or n=1)
2. inductive step- assume it's true for n=k, and then prove it's also true for n=k+1

if both steps work, the statement is true for all natural numbers.

how they relate:

- inuction proves that a recursive function is correct for all inputs. 
- you can define functions recursively, and prove their properties indictively. 

analogy-

- recursion = gow do i solve this step based on much smaller steps?
- indiction = how do i prove this step works based on smaller steps. 

uses of recursion in cs:

concept                      use of fibonacci
recursion                   intro to recursive function design 
dynamic programming         
fibonacci heap
complexity
algorithm analysis

Uses of matrix multiplication in cs:

- image processing 
- machine learning
- graphics and 3D rotation 
- data compression and linear transformations 

key properties 

- multiplying matrices are associative, distributive, and not communicative

special types of matrix multiplication 
- transpose 
- inverse 

what it matters for 
- graphics- rotation, scaling, projection in 2d/3d
- ML/AI- matric math is the foundation of backpropagation and gradient descent 
- Graph Theory- adjacency matriced use 
- Search Engines- Ranking algorithms use matrix operations 

Use pytest to write a unit test for your HTTP Assignment repo (for the exponents of 2)

6/16

A decorator is a high order function that wraps another function to extend or modify its behavior without changing the original functions code.

- basic decorator pattern:

decorator(fn) takes a function as an input
it returns wrap, a new function that:
- logs the og function
- calls fn with whatever arguments were passed in  

the .apply(this, args) preserved context and passes the argument correctly 

useful for: debugging or adding logging around any function 

- time decorator (synchronous)

- records the start and end time of the functions execution 
- logs the timew taken in ms

useful for: measure performance of CPU= heavy operations (e.g. sorting, loops)

- time decorator (async version)

same as the sync version but works with async functions 
uses await to make sure it measures the full tyime of the async call

useful for: time http requests, set timeout, database calls, or file reading 

- memoize decorator (caching results)

stores reviously computed results in a cache (lookupTable)
if the same input is seen again, it skips recomputing and returns the stored results

great for recursive functions like fibonacci, or expensive calculations that get repeated.

- once decorator 

allows a finction to only run once 
cached the result and reuses it for all future calls

useful for initializing logic, singleton pattern, or one-time configuration 

- trottle decorator

ensures that fn is only called once per interval ms
ignores extra calls that happen too soon

uses: limit how often a finction can run (e.g. prevent API scam or UI overload from rapid clicks)

- after decorator 

ignores the finction call until its been triggered count times 
after that the finction runs normally 

uses: only shows a popup/ help tip after the user has performed an action multiple times 

- debounce deocorator 

delays the function until the user calling it for interval ms
restarts th timer every time the function is triggered 

use: wait intil typing stops beofre sending a search requests. prevent rapiud button clicks 

- curry decorators 

transforms a function so it can be called one argument at a time 
returns a new function until all arguments are provided 

use: functional programming, patrial application, clean and resuable code composition 

bigint fionacci with parametrization 

- JS numbers are only precise up to Number.MAX_SAFE_INTEGER. to go beyond that (e.g., 79th fibonacci) we use BigInt


In my code we used:

@lru_cache (least recently used cache). irt is a memoization decorator that automatically caches the results of function calls based on the argument passed to it

ssh ac.ballen@login1.chicago.kbase.us

ssh-keygen -t ed25519 -C "bridgettallenn@gmail.com"


# SSH configuration for dev1
Host dev1
  HostName dev1  
  User ac.ballen
  IdentityFile ~/.ssh/id_ed25519
  IdentitiesOnly yes

# how to reconnect dev1 to repo

1. log out, back to home directory
2. ssh-add -l
3. ssh-add, enter passphrase
4. ssh dev1
5. ssh-add -l
6. cd bridgetallencontigfilterappdemo/
git status, git push \

def test_invalid_params(self):
    impl = self.serviceImpl
    ctx = self.ctx
    ws = self.wsName
    # Missing assembly ref
    with self.assertRaises(ValueError):
        impl.run_bridgetallenContigFilter_max(ctx, {'workspace_name': ws,
            'min_length': 100, 'max_length': 1000000})
    # Missing min length
    with self.assertRaises(ValueError):
        impl.run_bridgetallenContigFilter_max(ctx, {'workspace_name': ws, 'assembly_ref': 'x',
            'max_length': 1000000})
    # Min length is negative
    with self.assertRaises(ValueError):
        impl.run_bridgetallenContigFilter_max(ctx, {'workspace_name': ws, 'assembly_ref': 'x',
            'min_length': -1, 'max_length': 1000000})
    # Min length is wrong type
    with self.assertRaises(ValueError):
        impl.run_bridgetallenContigFilter_max(ctx, {'workspace_name': ws, 'assembly_ref': 'x',
            'min_length': 'x', 'max_length': 1000000})
    # Assembly ref is wrong type
    with self.assertRaises(ValueError):
        impl.run_bridgetallenContigFilter_max(ctx, {'workspace_name': ws, 'assembly_ref': 1,
            'min_length': 1, 'max_length': 100

Wednesday 6/25

OSI Model 

open systems interconnection model - gives a basis for the coordination of standards development for the purpose of systems interconnection 

components of the copmmunication system 

1. physical layer 
2. data link layer 
3. network layer
4. transport layer
5. session layer
6. presentation layer
7. application layer

SQL Notes - june 26

SELECT * = retrieve all of the data from the columns 

concatenation operator || to concatenate the first name, space, and last name of every customer.

you can assign a column alias full_name to the first column of the query

6/27 Unit testing and TDD

unit testing is the practice of testing individual parts if the code - usually finctions or methods - to make sure they work correctly insiolation 

TDD- write tests before the code 

unit tests:

- input/output behavior: does the function return the right results 
- edge cases: empty input, huge input, incorrect types 
- exceptions: does it raise an error when it should 

Ideas for the LLM Test; 

test for valid input, invalid or currupt input, if there's a missing file, if its the wrong file format, to accept parameters. 

Indentation rules for python 

1. every block (after a colon) must be indented
2. lines inside of a block must have the same level of indentation 
3. all looped lined stay together 
4. inside if, else, elif
5. inside for and while loops 
6. insid def or class
7. when you nest structures each new block indents again 

leet code problems

inorder tree traveral 
- from typing import Optional, list

this line imports type hints: Optional[treenode]: means the value can be a TreeNode or None
List[int]: the function will return a list of integers 

class treenode:
defines a binary tree:

def __init__(self, val=0, left=None, right=None):
    self.val = val
    self.left = left
    self.right = right

val = value in this node
left = pointer to the left child (another treenode or none)
right = pointer to the right child 

class solution: a container where we define the method (as per LeetCode-stlye questions)

def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
defines a function to perform in-order traversal (left -> node -> right) and return a list of visited node values 

stack = []
a stack is used to simulate recursion 
it stores nodes we're visitng, especially while walking down the left side of the tree

result = []
this list will store the final result - the node values in in-order sequence.

current = root 
start the traversal at the root of the tree 

what is a stack 

- abstract data type that serves as collection of elements with two main operations 

push- which adds and element to the collection and 
pop which removes the most recently added element 

the stack is an analogy to a set of physical items stacked one atop the other  

iterative vs. recursive 

iterative- uses loops (for, while), repeats a clock of code until a condition is met , usually releis on manual control (like a stack)

recursive- a function calls itself, automatically uses the call stack to keep track of progess, requires a base case to stop recursion 

different kinds of loops 
a for loops is for when you know how many times you'll loops ahead of time

for the binary tree you have to run until everything is processed which is what a while loop is for. 

nested loops- the nestedloops split the traversal into two phases:
- go as far left as possible 
- backtrack one node at a time 

outer loops purpose = keep processes nodes as long as we've not reached the end of the tree or there are still nodes saved in the stack that we havent visited

inner loops purpose = go all the way dowwn the left subtree

Unittest.mock

allows you to replace parts of your syste munder test with mock objects and make assertions about how they have been used. 

provides a core mock class 

mock provides a patch() devcorstor that handles patching module and class level attributesd within the scope of a test, along with mentinel for creating unique objects 

mock is designed for use with unittest and is based on the "action - assertion" pattern 

the patch function can be used as a decorator or a context manager to replace the target object with a mock diring the test. the target is specified as a string in the form 'module.ClassName'.

a context manager uses a with statement to temporarily change something just inside a block of code. outside of the block everything goes back to normal 

a decorator chanfed the behavior for the entire function it decorates.

http= hyper text transfer protocol 

tmux - lets you manage multpile terminal sessions from one window. 

       def test_intersect(self):
        # in the test, use print() to put things in stdout
        first_file = 'GSE203496_xmoo1_line_pooled_assembly.gff'
        second_file = 'GSE240325_apo_rbfox_insitu_clustered.sorted.filtered_lite.gff'
        self.serviceImpl.run_kb_bedtools_intersect(
            self.ctx,
            {
                "workspace_name": self.wsName,
                "first_file" : first_file,
                "second_file" : second_file,
                "output_name": "intersectOutput",
            }
        )


                # - download report
        # - assert that the report has expected contents

    # def test_bam_to_fastq(self):
        # in the test, use print() to put things in stdout
        # bam_filename = 'wgEncodeUwRepliSeqBg02esG1bAlnRep1.bam'
        # staging_path = '/data/bulk/dpvs2004/'
        #pathlib.Path(staging_path).mkdir(parents=True, exist_ok=True)
        # output = BamConversion.bam_to_fastq(bam_filename)
        # copyfile(output, os.path.join(self.scratch, 'out.fq'))
        # with subprocess.Popen(f'ls -halF {self.scratch}'.split(' '), stdout=subprocess.PIPE) as proc:
            # proc.wait()
            # print(proc.stdout.read())
        #bam = BamConversion(ctx={}, config={"clients": {DataFileUtil=DataFileUtil, KBaseReport=KBaseReport,
        #       ReadsUtils=ReadsUtils}}, app_config={}),