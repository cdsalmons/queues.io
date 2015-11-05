# [Queues.io](http://queues.io)

![screenshot](https://s3.amazonaws.com/f.cl.ly/items/3B1k0I2b120K1O0c1P3C/queues-io-2.png)

There's a lot of libraries in many different languages, using various
technologies, implementing "queuing".

All of them are different and were created out of certain need. The purpose of
this project is to collect them all in one place with resources about them.

# Developing

Right now project is based on one simple `erb` template and `projects.yml` file
with all of the data. Template is rendered and saved to `public/` folder as
static html file using:

```
$ bin/compile
```

# Deployment

```
$ bin/deploy
```

You need to install and configure `s3cmd` utility first:

```
$ brew install s3cmd
```

# Contributing

## Guidelines

I want queues.io to be opinionated page with quality resources about queueing
projects. To achieve this I wrote some bullet points I'd like people stick with
when adding new stuff:

  * Project should consist of `name`, `summary`, `url`, `tags`, `links`
  * There should be at least one tag, which should be language/technology in
    which it was created. Other tags can describe for example database used on
    which solution is based (like redis or postgres)
  * There should be at least one link about the library
  * Links should not point to documentation, client libraries or wiki pages.
    They should be well written, valuable blog posts, articles which are harder
    to find than resources provided by creators.

## Github workflow

I would like this to be a community effort. If there's any lib missing, or you
know cool links to articles/videos/slides about ones that are listed, feel free
to add them. I open for any contribution.

  1. Fork it
  2. Create your feature branch (git checkout -b my-new-feature)
  3. Commit your changes (git commit -am 'Add some feature')
  4. Push to the branch (git push origin my-new-feature)
  5. Create new Pull Request

## Quick Cheat Sheet

These 3 messaging technologies have different approaches on building distributed systems :

RabbitMQ is one of the leading implementation of the AMQP protocol (along with Apache Qpid). Therefore, it implements a broker architecture, meaning that messages are queued on a central node before being sent to clients. This approach makes RabbitMQ very easy to use and deploy, because advanced scenarios like routing, load balancing or persistent message queuing are supported in just a few lines of code. However, it also makes it less scalable and “slower” because the central node adds latency and message envelopes are quite big.

ZeroMq is a very lightweight messaging system specially designed for high throughput/low latency scenarios like the one you can find in the financial world. Zmq supports many advanced messaging scenarios but contrary to RabbitMQ, you’ll have to implement most of them yourself by combining various pieces of the framework (e.g : sockets and devices). Zmq is very flexible but you’ll have to study the 80 pages or so of the guide (which I recommend reading for anybody writing distributed system, even if you don’t use Zmq) before being able to do anything more complicated than sending messages between 2 peers.

ActiveMQ is in the middle ground. Like Zmq, it can be deployed with both broker and P2P topologies. Like RabbitMQ, it’s easier to implement advanced scenarios but usually at the cost of raw performance. It’s the Swiss army knife of messaging :-).

Finally, all 3 products:

have client apis for the most common languages (C++, Java, .Net, Python, Php, Ruby, …)
have strong documentation
are actively supported

## Message Queue Servers

Message queue servers are available in various languages, Erlang (RabbitMQ), C (beanstalkd), Ruby (Starling or Sparrow), Scala (Kestrel, Kafka) or Java (ActiveMQ). A short overview can be found here

Sparrow

written by Alex MacCaw
Sparrow is a lightweight queue written in Ruby that “speaks memcache”
Starling

written by Blaine Cook at Twitter
Starling is a Message Queue Server based on MemCached
written in Ruby
stores jobs in memory (message queue)
documentation: some good tutorials, for example the railscast about starling and workling or this blog post about starling
Kestrel

written by Robey Pointer
Starling clone written in Scala (a port of Starling from Ruby to Scala)
Queues are stored in memory, but logged on disk
RabbitMQ

RabbitMQ is a Message Queue Server in Erlang
stores jobs in memory (message queue)
Apache ActiveMQ

ActiveMQ is an open source message broker in Java
Beanstalkd

written by Philotic, Inc. to improve the response time of a Facebook application
in-memory workqueue service mostly written in C
Docu: http://nubyonrails.com/articles/about-this-blog-beanstalk-messaging-queue
Amazon SQS

Amazon Simple Queue Service
Kafka

Written at LinkedIn in Scala
Used by LinkedIn to offload processing of all page and other views
Defaults to using persistence, uses OS disk cache for hot data (has higher throughput then any of the above having persistence enabled)
Supports both on-line as off-line processing
ZMQ

The socket library that acts as a concurrency framework
Faster than TCP, for clustered products and supercomputing
Carries messages across inproc, IPC, TCP, and multicast
Connect N-to-N via fanout, pubsub, pipeline, request-reply
Asynch I/O for scalable multicore message-passing apps
EagleMQ

EagleMQ is an open source, high-performance and lightweight queue manager.
Written in C
Stores all data in memory and support persistence.
It has its own protocol. Supports work with queues, routes and channels.
IronMQ

IronMQ
Written in Go
Fully managed queue service
Available both as cloud version and on-premise

# [Thread](http://stackoverflow.com/questions/731233/activemq-or-rabbitmq-or-zeromq-or?rq=1)
