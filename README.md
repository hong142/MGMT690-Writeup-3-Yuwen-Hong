# Object Detection with Tensorflow
## Intro to Neural Nets
Replicate human brain
A complicated function any machine learning model we talking about
Give some inputs and get uptput
General structure is the same, you give it one or more inputs and you get output.
A series of inputs, picturis in four, and we 3, different numbet. Put in get out.
How we set up this function is a network of this subfunction. Each one of this code on code nodes,is just another function- a seconf function, a subfunction embeded in the big function, we provide this inputs, and when they get to this little nodes, you can see here in the senicnetha twe havesomething kikek this, heres my nodes, three inputs and something comes out. Another function, numnerical inputs, take those into function get another output, add this things up in some way, lets call this x1 x2x3, and this is my ooutput, my just adding my combianing in a certain way and add a constant, the only difierntce is we are actually appliying an overall function to those to intrude nonlinearity.we have an overall function, input left output right.intrenally we are just adding things up ina bunch of different spot sto produce output.
Combaining things ina lot of different way like that.flexbility, what I have here creating abunch of this nodes and notivcing each one of this nodes have anumber of things Ican change, weight and bias, each one of those nodes has a series of this I can tirst and tune. What I assumingthe network there exigst some relationship bwteenwhat I puin and what I want to get out. Like I’m putting in a image, I’m want ing togetout a detected object, I’m putting in a series measurmentof flowers and want toget out the spicies of the flower.I’m assuming theres some relationships between, I just don’t know what they are. By thsithings in this way, I get this very flexbile way in combaining in the inputs, change thoses values until I totally mimic the relationship. The number generate through the machine learning process, the model that we’ll  use to do object detection has been trained by tons of different images and that’s whatleads to this weigths, when you have thisweight, we can just start to punoping thing sthorugh the left side and getting results at the right side using previdoly trained wieges and bias. As previously mention the way that we find the mmodel is by twking those numbers up and down until we find the ones actually mimic those relationships, and that’s called trainging procees. Specific formolizam around how we can find them, not just randomly move up and down until we find them. 
Regardless what the network si using, assuming there are soemrelationship. It might be arealy complicated relationship. Humnas can’t understand, which is what the networks find. FI theres no relationship, one of those b=garbage in and garbage out relationship, your model training might not coverge, because it just not able to find a suitable relationsip. It could be either an indiation that you network is not complicated enough to detect that relationship, or thatyou don’t have the right data.(right features to describe the realtihnsip you want to model.
Fully connected network, passing through, each of those nodes do the same thing. Hidden layer, adding extra complixety that I can model. So the model layers you add the more complicated your lrelationship, although a single hidden layer is likepwoerful enough for majority of classification task. Somehat a balckbox approach, understand magnism here, when I get whte weights and bais, thetr is no way to undertand. 
Setup my node does this. When training , maek random choice, not right, change until get difrent ones.Randomly chose this. Ones find a good output that’s a trained model. -combination of the definition of this function and a primaterization of thise tow numnders.y=mx+b, 
Simple architecture, how I arrange this node and how I DEFINE THEM IN THIS WAY. Ther is a ot of other ones, a buch of hiden layers. These a different fuctions. Number of nodes, number of feaures, out puts probability of each of speices.
Strictly defined whre the nodes are, as soon as you adding more and more hidenlayers, you getout of 1000 premiteres, tis hard to say whay each one is what.

## Intro to Tensorflow
Tensorflow, what it is. software project , people use it often from pyton, c++, came out of goole, they hwta to do this like this at very large scale,like google type scale. Nureonetwotk and large optimization and other types of machine leaning and other tyoes ofo umnerical computing. Internally fro goole  speech recongnition, products or inreaseingly their image RECOGNITION PROJECTS.
### Why Tensorflow
1. Portable
WHY its useful. Sekerterlerna, often time not scale to large, frailty restictlyve in terms of what you can runn it. You have to run it sowmwhere you can intstill secilaern. Doesn’t work on all systmes, one thisn tnesoflow make it more portal is  graph-beased computation. Turns out that any sort fo operation you do on computer can be rperntitve as a graph, including function, more comp;lciation function. Overall function can be reprpesnted as a graph of computation. This happends and that results is paased under this pass this operation which does this that does that. You can see here is one of the inputs e have this next bit is like a certain type of this function here helps in adding all this toethet. The next the   layer is next function.ohter things on top,like grediens. Trainig model. Finding this weigngs by combiang things, figuring of how fra its off. In tensoerflow its not represented purely just by the function wirte in code,whenyou actually runtensofelow code, it generates the graph under the hood and one of reason useful,is if you break things down to the grapoh form, it actuallymakes your compalied code very protable in a sense that at its lowest level any function can be represented by this graphand each of this operation is very well defined. If you want toimplement this on a lynix system or windowsmac, all of this underline things can be reprented in that architecture which aloows you toprot that computational staff to a bunch of diferetn envoerinmen(deifernt arctectur)t, so you can run it .. 
2. Distributed,Flexible
second, makes not where you can run it but alos how you can run it. By how I mean is if you llok at someof this things have to excuted before other things, someof them can runsimulatenaously, setting things up in this graphical representation, you can actually separate things out different steps,across even different machinines. So you can actually seof a tensorflow cluster composed of many difernt cpu machines, insteancs in the cloud, you can distrubte those processing stpes across thosethen you can run it mre faster than you would if you runall of the steps on a single computer. Distributed. Flexible is can distributed things in differntways like you on a gpu vs cpu or a cluster of cpus vs a number of virtual code on your computers . different wyas you can accelerate this stpes. 
You defie the stpes, it generate a graph, intermidean representation. If you running on a gpu, you point me to a gpu library, I’m gonignto exectute in this way. Optimize for that acrutecture. Or if you present this graph to that seriese of meachines, if would say on you want me to execute like a series of cpu instances, this is the way I should execntue. 

3. Active, Supported
Another thing why tensorflow, is extreme active product, 76stars on github, if we look at the 141 open commits evertyh snlge day on the project, actively making it better, fixing bugs.

Supported. Active community, there thousands of people working on it everyday. Slack channel, github issues, you going to get responsequicklyask a question, wenot gon implements that, you get an answer, if it’s a bug, it work just because it so large companies. For our context, inprevious write uo, we like a team,tryoing to implemte this pipeline to do analytic security,object detection tensoflowhas like knid etnkey support for object dection api, has an really nice interface wit that, google devepoled tons of models forthis, in tensoflwowhich we can utilize out of the box. And its very well-documentd for that sort of interaction, so its very low barrier of entry to do object detection and its obvoulsiy paired with the fact that its very protable. We canexcetue in a distributed way. Appleing. Free.

Tradeoff,using open sourcing things. Don’t have get token or key for everybody.don’t have to pay anything.
Have to sing up with them, mysetting paying hundred and thousnads of dollars.
Cost versus robustic and customer support. I can’t call up someone in the googlwe for a problem and expect to be solved in two hours. When you using op projects, ow cost to entry, be careful with whigh oopen source project to choose, we want to bein an active community center around tooling is also active. You woun’t necessarily want to choose it if its not compatible with those envioenment, if we want aws. Avarious consideration you want to taking into when you choose open souecre. 
The trend in analytics industry is towards opned source in genral. And if you really ned, tere is ton dos of compamy you can paid to get posted solutions, advising.

4. Nice Object Detection API
The tensorflow object detection api. The tensofloerproject ingenral is very flexble,a lot of difernt things. You can do noureo networks , you can do statsics,optimization, detection. Peole have use tensoflow very wide for object detection. The use this basically, you can see under the main tensoferlow, visually suoprt one, python packae let  you get into tensoflow in object detection centric way. Package you want use. Extra layer of convience rather than start atsrcach with nice convient tooling they already build. Cuasige tnedoflow is a huge learning curve, you can do anything with it. If you create a project,.api ,like a package.(varies way of interac, you can do it like a package, you can also seta server you can interact with. Like a Jason http requrst, or like a notebook send imges through)provides more flexibility, call pai instead of package. Skenle maching learning, realiy heaveuliy on numpy. Reauiqre a lot more effort.
There is varies non-object detection related image things, taking a picture craupted. Filing tehdetails. Or trasfreing to a map. 
You implement machine learning models in tnesoflow,it’s a platform fro mach learning. You will utilize a model that has been implemented in tensoflow. But tnedoslt flow is more general, more like a numpy. Platfolw. Implement .Decision tree, logistic regresstion , allthose things. 
Advantage. If you doing it on a single machine, it might be a little bit faster, if you wna tot distribute machine learnig or do some type f imge-baed processing, those in genral want people tend to tnedsoflow. If you can implement within half an hour, no reason turn to tensoflow for simplicity. Unless you are looking fro convience around image processing sort of things. 
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
based on our previous conversations, is that a good way to approach, delpy these code, run this python code in apipeline, what missing, have to get data to these code, login like we just did, copy it over, what we will do. This is the same problem like running things on laptop, we don’t want loging in th emidel of night and copy code over, or copy data over, run the code maunlly. We are working on a clould , not quite the level we want to achieve in the full pipieline.for full, we going to running things on an instance similar to these, but we are goingto automate moving data to it,running it. So we should never hsvev tologing every time youo nat run something. The problem is like we going to a a couple of preprocess steps, we have inferanec step, a couple post processing steps, what we don’t want to do is to spine up  abounch of this instance , loging to each one, copy the code and data to eahcone,run one bite of code, gather the results, copy that up to the other machine, run that maunully, copy that to the next machine, not sustaibale. In the right direction, not run this on laptop, but not what we eventually would be. 
Show you how tensoflow works, how to run it. Is gone be automated. Now experiment pahse, how we run, the nautomated. We using tenfoelow for this reasons , this is howwe are going to run tensoflow from python. Calling in tf inpython, similar to calling a pacakge. Tf will generate pragh, calling c++, the interacfe is just like intract with a package. Cal someother libairiy related to io and someother datatypes. 
If you train a model in tf and fit in prarmeters and you want o save the model for later, protobuff file.  Teling where my model is defined, weights and bias and how to run the network. What we will generate out of the model this an object of that image corresponse to label 445, and the label map tell where the 445 is ,people, cat. Pb ifle
Tf.graph, computation graph, importing graph, loading label map. Helper function, uting images in 
Reads in, transle to numers of clors, briagness ,rgb, converting imges to numbers, what feeding in the left side of graph.  Where the images are that I want to detect something. Detection on all the image in that folder image before, definig the size of the output images, coinvience in saving output images. Point to all the refrences thins,hers model, hereslabels, size of  images out, let actually do something.
Seesion.
Input our image, convert to a tensofr , a set of numbers. A tensor is a multi level marix, rather than having one matrix representing color, one repts  brignrsness. So defining those 
Looking over all the imgaes, for each , load into a numpy array, and detect the classes,utilize this fucntions to label on the image, whre the class is and what it is. Save those outptuimages to imge after. 
Loading models from a file, loading labels form afile, telling to detect object nad models in afoler, and loop over images and ouptput another inage with the little box drwops where the object is. Visualize box and label on arragu of image. Convience build into this api, people want to do the sort fo things a lot, we don’t want to write it from srach. Able to do this in a very short amount of code, beaucse tf already have thes nice api to do this. We don’t aste abuhcn of time to imeplementing things. 
Already trained model, we’ll tlak about how to expand it, whrer we put training in. right now, gollge has create this model, if we want to trian the model on asset of certain images, intruder, but those models are firatly robst in thismmoment, assume now the arctuectur is good. 
Jip image, copy url wg url, pull down the image
Mapping things in ft floder will show up in docker image. Environment whre we run tensorflow. 

