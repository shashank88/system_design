# system_design
*Preparation links and resources for system design questions

I collected and studied from a lot of links while preparing for interviews this year and realized that unlike coding questions which has plenty of good repos and combined resources , system design remains elusive. People end up reading from scattered resources and might get pigeon-holed into studying one specific domain and get tongue tied when answering such questions.

#Disclaimer : I am not a system design expert and do not have a ton of experience in this domain , but over the course of giving interviews , reading up from many different sources have a decent idea of what to study and how to answer such questions . This is a domain that can take year to master even one facet of system design , hence I would recommend instead of spending too much time on one topic , try to spread your time , get a broader overview of the entire domain then go into what you might be working on or what interests you more. (Also depends on who are you interviewing with and the level you are interviewing for). Also I have never been in an interview for mobile app dev so dont have much idea on that , feel free to send pull requests with that section also.

#Where to start from?

For a very broad overview please go through these lectures , really useful:
* [david malans cs75 scalability talk](https://www.youtube.com/watch?v=-W9F__D3oY4&list=PLmhRNZyYVpDmLpaVQm3mK5PY5KB_4hLjE&index=10)
Feel free to go through other lectures if needed. 

* [david huffman's talk , scaling up talk](https://www.udacity.com/course/web-development--cs253)

These talks should give you decent ammo to start formulating some architectures yourself . But before you begin , here are some topics(in no particular order) which in my opinion you should have a decent idea of before proceeding.

1.Operating system basics: how a file system , virtual memory , paging , instruction execution cycle etc work
(For starters silbershatz should be enough , if you already have decent knowledge try stallings book on OS)
2. Networking basics : 
Should know the TCP/IP stack , basics of how internet , HTTP , TCP/IP work at the minimum . cs75 on youtube (1st lecture ) should give a broad overview . I personally love [networking-a top down approach](http://www.amazon.com/Computer-Networking-Top-Down-Approach-Edition/dp/0132856204) .
3. Concurrency basics : threads , processes , threading in the language you know . Locks , mutex etc . 
4. DB basics: types of DB's (sql vs no sql etc ),hashing and indexing , EAV based dbs . Sharding , caching for dbs , master slave etc
5. A basic idea of how a basic architecture is , say load balancers , proxy , servers , db servers , caching servers , precompute , logging big data etc. Just know broadly what is each layer for.  
6. very basic summary of what the [CAP therem](http://robertgreiner.com/2014/08/cap-theorem-revisited/) is (Have never been asked about the theorem itself , but knowing it will help you in designing large scale systems. 

# How to answer in interviews
I found [hiredintech](http://www.hiredintech.com/system-design) videos an excellent place to start with . The way how to approach a design question as given in the link is really useful . It goes into how we start with clearing the use-cases of the system , then thinking in abstract manner of the various component and the interactions . Think about the bottlenecks of the system and what is more critical for your system ( eg latency vs reliability vs uptime etc) Address those giving the tradeoff of your appraoch. 

[system design in crack the coding interview](http://www.flipkart.com/cracking-coding-interview-150-programming-questions-solutions-english-5th/p/itmdz4pvzbhcv6uv) : good approach on how to begin attacking a problem by first solving for a small usecase then expanding the system .

The best way to prepare for such questions is do mock interviews , pick any topic (given below) try to comeup with a design and then go and see how and why it is designed in that manner. There is absolutely no alternative to practice!! Whiteboarding a system design question is similar to actually writing code and testing it ! Just reading will only take you so far.

# Steps how I approach the system design questions in interviews

These are the steps I go through mentally in the interviews , followed by actual interview experiences:

a) Be absolutely sure you understand the problem being asked , clarify on the onset rather than assuming anything 
b) Use-cases . This is critical , you MUST know what is the system going to be used for , what is the scale it is going to be used for .
c) Solve the problem for a very small set, say 100 users . This will broadly help you figure out the data structures , components , abstract design of the overall model
d) Write down the various components figured out so far and how will they interact with each other.
e)  As a rule of thumb remember atleast these :
 1. processing 2.storage 3.caching 4.concurrency 5.security 6.load balancing and proxy 7.CDN 8. Monetization
 
 eg . What kind of DB (will mysql do ? or nosql fits btr? ) , do you need caching (almost always !) and how much , is security a prime concern? 
f) Special cases for the question asked. Eg say designing a system for storing thumbnails , will a file system suffice ? What if you have to scale for facebook or google? Will a nosql based db work?(BTW Check this out [Haystack](https://www.usenix.org/legacy/event/osdi10/tech/full_papers/Beaver.pdf)
g) After I have my components in place , what I generally try to do is look for minor optimization in various places according to the usecases , various tradeoffs that will help in better scaling in 99% cases .
h) Check with the interviewer is there any other special case he is looking to solve ? Also it really helps if you know about the company you are interviewing with , what its architecture is , what will the interviewer have more interest in based on the company and what he works on ? 

# Common Design questions :
It generally depends what you are and you will be working on . Also what your level is but these are some of the more frequent interview questions .

* Design a news feed (eg facebook , twitter ) : [news feed](http://www.quora.com/Software-Engineering-Best-Practices/What-are-best-practices-for-building-something-like-a-News-Feed)
* Design a product based on maps , eg hotel / ATM finder.
* Design amazon's frequently viewed product page
* Design an online poker game for multiplayer . Solve for persistence , concurrency , scale .
* Design a url compression system
* Search engine ( generally asked with people who have some domain knowledge ) : basic crawling , collection , hashing etc. Dependes on your expertise on this topic
* Design dropbox's architecture . [good talk on this](https://www.youtube.com/watch?v=PE4gwstWhmc)
* Design a picture sharing website . How will you store thumbnails , photos? Usage of CDNS? caching at various layers etc .
* Design malloc , free and garbage collection system . What data structures to use? wrapper over malloc etc
* Design a site like junglee.com i.e price comparision , availability on ecommerce websites.
* A web application for chatting , eg whatsapp , facebook chat . Issues of each , scaling problems , status and availablility notification etc.
* Design a system for collaberating over a document simulataneously (eg google docs)
* 

# Architecture and engineering blogs of various companies:

Personally I looked into the following architectures:

* [Google file system](http://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)
* [facebook haystack needle architecture](https://www.usenix.org/legacy/event/osdi10/tech/full_papers/Beaver.pdf)
* [facebook graph api]
* Basics of google search
* youtube architecture and optimizations for video
* Twitter and facebook feeds
* [Instagram](http://instagram-engineering.tumblr.com/post/13649370142/what-powers-instagram-hundreds-of-instances) and other image based social networks
* 

# Recommended links and books

good site for getting overviews of architectures : [highscalability](http://highscalability.com/)
Broad overview of system design :[system design issues](http://highscalability.com/blog/2014/5/12/4-architecture-issues-when-scaling-web-applications-bottlene.html)

