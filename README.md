# Object Detection with Tensorflow
In previous writeups, we've discussed our team's plan to develop and implement a pipeline for security system object detection analyses, and we've covered the setup of data storage and organization. Our next focus is the analysis and machine learning process. This writeup introduces Tensorflow, the software we are going to use for the process, based on why we choose it and how we use it. 
## Intro to Neural Nets
Before we talk about the Tensorflow, we need to briefly introduce the concept of 'neural network', becuase its our choice of approch for our model building. In artificial context, it means a network of nodes connected in a way similar to the biological neural network in a brain. The picture below shows a relatively simple neural network example. Basically, the whole network represents a function used in the machine learning process, with each node represents a sub-function. The left side is input layer and each node represents an input (feature). The data pass through those functions to reach the right side, which gives us the output. More complication can be added to the network if more hidden layers is added, although a single hidden layer is powerful enough for majority of classification tasks.

The assumption here is that some relationships exist between input elements and output elements. We define the inputs, outputs and a basic structure. The network is going to figure out those relationships for us, in other words, getting the proper weights of each inputs as well as bias for the ultimate function.

There might be several reasons you can't get the relationship out of the network. Typically, it's either because you don’t have the right data, which are right features to describe the relationship you want, or because your network is not complicated enough to detect that relationship.

By combining things in a lot of different ways, we get flexibility in combining inputs. The process of randomly changing weights and bias until the function totally mimic the relationship is what we called “training process’, a combination of defining the function and parameterization of inputs. The function providing a good output is a trained model. 
## Intro to Tensorflow
The analysis model we want to build is about object detection and we want to do it through a neural network. Currently, Tensorflow came out of google is a good choice, because it was designed for very large scale analyses, including those using neural network.
### Why Tensorflow
1. Portable
One of the advantage of Tensorflow is its portableness. It uses graph-based computation, in which any sort of operation you do on a computer can be represented as a graph. Here is an example of graph representation of a complicated function. 

When operations are broken down into the graph form, your complied codes are portable as any function at the lowest level can be represented by this graph and is well defined. You can implement the computational stuff in almost any environment. On the other hand, Scikitlearn, another commonly used free software library for machine learning, has many restrictions on input, scale and running environment. It requires systems that can install the software and can only run certain types of data on a relatively small scale. 
2. Distributed, Flexible
Another advantage of Tensorflow due to its graphical representation is that works can be distributed and in a flexible way. You may have noticed that while some of steps in the function have to be executed consequently, some of them can run simultaneously. By setting things up in graphics, we can separate different steps, and distribute them across different machines or instances in a cloud, so that we can expect to run things much faster than we would if we run all of the steps on a single computer. Moreover, depends on the architecture or environment we assigned, we get the flexibility to distribute things in varies ways to accelerate the process and get optimization for the assigned architecture. It doesn’t matter whether the architecture is a GPU or CPU or a cluster of any of them.
 However, in general, we only use Tensorflow for distributing machine learning or image-based processing. You probably don’t want to turn to Tensorflow if you can finish the implementation shortly on a single machine. Otherwise, instead of saving time, you may actually generate extra trouble for your implementation.

3. Active, Supported
Another thing why tensorflow, is extreme active product, 76stars on github, if we look at the 141 open commits 
evertyh snlge day on the project, actively making it better, fixing bugs.

Supported. Active community, there thousands of people working on it everyday. Slack channel, github issues, you going to get responsequicklyask a question, wenot gon implements that, you get an answer, if it’s a bug, it work just because it so large companies. 



Tradeoff,using open sourcing things. Don’t have get token or key for everybody.don’t have to pay anything.
Have to sing up with them, mysetting paying hundred and thousnads of dollars.
Cost versus robustic and customer support. I can’t call up someone in the googlwe for a problem and expect to be solved in two hours. When you using op projects, ow cost to entry, be careful with whigh oopen source project to choose, we want to bein an active community center around tooling is also active. You woun’t necessarily want to choose it if its not compatible with those envioenment, if we want aws. Avarious consideration you want to taking into when you choose open souecre. 
The trend in analytics industry is towards opned source in genral. And if you really ned, tere is ton dos of compamy you can paid to get posted solutions, advising.

4. Nice Object Detection API
For our context, inprevious write uo, we like a team,tryoing to implemte this pipeline to do analytic security,object detection tensoflowhas like knid etnkey support for object dection api, has an really nice interface wit that, google devepoled tons of models forthis, in tensoflwowhich we can utilize out of the box. And its very well-documentd for that sort of interaction, so its very low barrier of entry to do object detection and its obvoulsiy paired with the fact that its very protable. We canexcetue in a distributed way. Appleing. Free.
The tensorflow object detection api. The tensofloerproject ingenral is very flexble,a lot of difernt things. You can do noureo networks , you can do statsics,optimization, detection. Peole have use tensoflow very wide for object detection. The use this basically, you can see under the main tensoferlow, visually suoprt one, python packae let  you get into tensoflow in object detection centric way. Package you want use. Extra layer of convience rather than start atsrcach with nice convient tooling they already build. Cuasige tnedoflow is a huge learning curve, you can do anything with it. If you create a project,.api ,like a package.(varies way of interac, you can do it like a package, you can also seta server you can interact with. Like a Jason http requrst, or like a notebook send imges through)provides more flexibility, call pai instead of package. Skenle maching learning, realiy heaveuliy on numpy. Reauiqre a lot more effort.
There is varies non-object detection related image things, taking a picture craupted. Filing tehdetails. Or trasfreing to a map. 
You implement machine learning models in tnesoflow,it’s a platform fro mach learning. You will utilize a model that has been implemented in tensoflow. But tnedoslt flow is more general, more like a numpy. Platfolw. Implement .Decision tree, logistic regresstion , allthose things. 

Graph dabses are more like a representation fo data, youcan utilize a connected graph to reproent dat relationa, b related c, c is related f, or you can use graph to reprente computation.
What we do here, graph reprented a series of logical computations. You can utilize graph databse to find those sort fo relationships. Itself doesn’t represent a computation. Social network, you need to store relationship, hard to store in object storage, you essentially have to stroe files toreprent, ragph databse, you can query, we are not here ask those questions. 
What we trying to do today. As prat of  our ovrall data pipeline we need to detect wht object in this images. How we gona do that, we gonna do that with tensorflow, why tensoflow, beachuse its nice in this ways, and you want motivate we wona utilize the object detection api in away similar to this, go through that, illustarate how to use object detection in api. The way we gonna use it now is silgit y difirent than use in automait pipeline, but it should motivate why we are doing somof that why we automate some of this stpes, why we deploy itin a way we are.

## Hands on with Tensorflow
Connect to a remote machine with a program called ssh, to get ssh serch for gitgit for window, MAC ON TERMINAL.
Instans in cloud, cloud vm. 
Bash command interaface, cammnds avialble is caleed basch shell.
Change Detreictoy to tf, moving around file system
In a computer in new York in digital oucen’s cloud. One of their instancs. Excecute in that machine in new York. Currently no periderm on machine, when we do the full dploy, ther wil be parkcyderm and cabernets. Here we are just focusing on running tensorflow and know what it looks like. 11 instance, own instance. Acees to the server.
Look up some codes calls tensorflow from python using the object detection api. See how that implemented, and run that code with tensoflow to detect ibject in an image. Under this flod another directory called code, cd to code, ls agaoin, theres is a pthon program another folder called model. On each of this instances, I want ahead and put the code we gonna run on the instance, and the things we gona need to run that code, 

Now experiment pahse, how we run, the nautomated. We using tenfoelow for this reasons , this is howwe are going to run tensoflow from python. Calling in tf inpython, similar to calling a pacakge. Tf will generate pragh, calling c++, the interacfe is just like intract with a package. Cal someother libairiy related to io and someother datatypes. 
If you train a model in tf and fit in prarmeters and you want o save the model for later, protobuff file.  Teling where my model is defined, weights and bias and how to run the network. What we will generate out of the model this an object of that image corresponse to label 445, and the label map tell where the 445 is ,people, cat. Pb ifle
Tf.graph, computation graph, importing graph, loading label map. Helper function, uting images in 
Reads in, transle to numers of clors, briagness ,rgb, converting imges to numbers, what feeding in the left side of graph.  Where the images are that I want to detect something. Detection on all the image in that folder image before, definig the size of the output images, coinvience in saving output images. Point to all the refrences thins,hers model, hereslabels, size of  images out, let actually do something.
Seesion.
Input our image, convert to a tensofr , a set of numbers. A tensor is a multi level marix, rather than having one matrix representing color, one repts  brignrsness. So defining those 
Looking over all the imgaes, for each , load into a numpy array, and detect the classes,utilize this fucntions to label on the image, whre the class is and what it is. Save those outptuimages to imge after. 
Loading models from a file, loading labels form afile, telling to detect object nad models in afoler, and loop over images and ouptput another inage with the little box drwops where the object is. Visualize box and label on arragu of image. Convience build into this api, people want to do the sort fo things a lot, we don’t want to write it from srach. Able to do this in a very short amount of code, beaucse tf already have thes nice api to do this. We don’t aste abuhcn of time to imeplementing things. 
Already trained model, we’ll tlak about how to expand it, whrer we put training in. right now, gollge has create this model, if we want to trian the model on asset of certain images, intruder, but those models are firatly robst in thismmoment, assume now the arctuectur is good. 
<img src="https://c2.staticflickr.com/6/5713/30364911106_56e2f1cd01_b.jpg" width="350">

Jip image, copy url wg url, pull down the image
Mapping things in ft floder will show up in docker image. Environment whre we run tensorflow. 

manually copying staff back anad forth from servers is annoying. 
based on our previous conversations, is that a good way to approach, delpy these code, run this python code in apipeline, what missing, have to get data to these code, login like we just did, copy it over, what we will do. This is the same problem like running things on laptop, we don’t want loging in th emidel of night and copy code over, or copy data over, run the code maunlly. We are working on a clould , not quite the level we want to achieve in the full pipieline.for full, we going to running things on an instance similar to these, but we are goingto automate moving data to it,running it. So we should never hsvev tologing every time youo nat run something. The problem is like we going to a a couple of preprocess steps, we have inferanec step, a couple post processing steps, what we don’t want to do is to spine up  abounch of this instance , loging to each one, copy the code and data to eahcone,run one bite of code, gather the results, copy that up to the other machine, run that maunully, copy that to the next machine, not sustaibale. In the right direction, not run this on laptop, but not what we eventually would be. 
Show you how tensoflow works, how to run it. Is gone be automated.
