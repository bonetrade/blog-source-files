+++

title = "Slides: Cultural Property Crime Seminar"
date = "2017-04-24T18:36:24+02:00"
type="slide"

theme = "night"
[revealOptions]
transition= 'fade'
controls= true
progress= true
history= true
center= true
+++

<table style="width:100%">
  <tr>
  <td align="left">
  <h2 style="color:#FFFFFF">fleshing out the bones</h2><br><h4>understanding the human remains trade<br>with computer vision</h4></td>
  </tr>
</table>
  
  <p align="right" style="color:#FFFFFF"> <small> Shawn Graham & Damien Huffer<br> @electricarchaeo  @DamienHuffer <br> follow along at j.mp/sg-dh-qm18
  </p>

---

<section data-background="museum-interior.png">

Note:
- late 19th century & scientific racism
- human zoos & the human cost

---

### Abraham Ulrikab
![](family.png)

Note:
- Abraham Ulrikab
- Moravian Christians in Labrador. Convinved to come to Europe to be part of a human zoo, because Abraham trusted, wanted to see Europe. Realized immediately the mistake. Kept a diary, translation of which was recently surfaced. Skulls and bones of him and his family found in museum collections in Paris & Berlin. Process of repatriation has begun

---

### How many other Abrahams are out there?

![](mosaic.jpg)

Note:
- every skull, every femur being traded was once a person. This trade dehumanizes, fetishizes, 'others', these people. Digital colonialism, revisits violence

---

### Our project:
- seeks to map this trade
- uses tools of digital humanities to understand both text and visual materials

---

when people want to buy bones, where do they go?

when people want to sell bones, where do they go?

Note:

given that much of this trade is morally dubious and legally in various grey zones

_how_ do they negotiate this sale?


---

> <small>'I have a pile of teeny human skull scraps laying around. Due to etsys rules i cannot sell human bone or make a listing but id love to do custom orders for anyone interested in a pendant, ring, etc made from a human skull fragment. Dm me! #bone #bones #skull #humanbone #humanskull #fragment #skullfragment #oddities #oddity.'
https://www.instagram.com/p/znHyR7AbXS/

![](skull-for-sale.jpg)

Note:
Not everyone is as bold as this. Most are aware that their _posts_ can be searched (ie key-word searching), and so rely on more subtle cues

On Instagram alone _where dollar values were named_

+ total amounted to approximately $190,000

+ the value of private sales cannot of course be known

+ Cultural impact: no.s of followers, following of _just those accounts that name a price_

+ a network with 138,014 individuals connected by 172,208 links

association with taxidermy, tattoo parlours - do i still have that cardiff photo?
three broad groupings: specialists explicitly interested in bones; generalists who follow the bones but also other things; and people who don't post pictures themselves but follow the bone accounts

---

![](screenshot-belgian-video.png)

Note:
video of man in Belgium degreasing a skull. Likely source for such a skull? WW1 battlefield. He's preparing it for cutting into an exploded view.

desecration of ww2 battleship wrecks - steel is pre 1945, so different atomic signature thus valuable; bones collected, given to the boss... what happens to them?

How do we deal with it?

Part of the problem is that not all of this is _illegal_. approaches and issues are of a part with broader trade in antiquities. Also: human remains are not property under common law!

broader trade tends to focus on the auction houses and the big collectors; smaller objects, ebay, etc do not attract as much attention

but the techniques developed to deal with these smaller items could be of significance for studying the broader trade, and the penetration of archaeological consciousness into the broader publics

---

## digital archaeology
### meets
## digital humanities

Note:

digital humanities approaches to data mining try to understand the contextual significance of what has been extracted

in our work, we have in the first instance scraped ~ 13 000 posts from one calendar year on Instagram (one of many places where human remains are traded); some posts were caught in the trawl as far back as 2013

we focussed on the _language_ the posts, building topic models and word vectors to understand some of the rhetorical constructions of buying and selling human Remains

---

![](vectors.png)

Note:
Exploring the vector space defined by binary pairs, 'good'-'bad', 'for sale'-'not for sale’. Hints of various dynamics at play can be viewed in contrasting, but related, terms, e.g. as with ‘acrylic painting’ falling in negative space and ‘skull decor’ falling in positive space. This might be a glimpse into the taste or aesthetic of those who create skull-related art, which may be important for understanding what creates the taste and demand for human remains themselves.

literal posts, 'human skulls for sale' do exist; but often the language is coded, more oblique, and seems to depend on the composition of the image itself to signal something for sale

---

## so that's what we've done

### here's where computer vision comes into it

Note:
our current research is looking at the composition of the images themselves, computationally. There are too many images to do the classificatory work ourselves. Some approaches to these kind of image classification or determinations of similarity employ 'human' computers like the Amazon Mechanical Turk service. There are serious ethical issues with employing that kind of labour on this material.

---


![](machine-visions-feature-matrix.png)
- Yannick Asogba, '[Machine Visions](http://clome.info/work/machine-visions/)'

---

![](machine-visions-neural-network.png)
- Yannick Asogba, '[Machine Visions](http://clome.info/work/machine-visions/)'

---

![](direct.gif)
- Carter [2017](https://techcrunch.com/2017/04/13/neural-networks-made-easy/)

---
![](pixplot.png)
- Yale DH lab, [code repo](https://github.com/YaleDHLab/pix-plot)

Note:
if however we stop the process just before the image labelling, we can use the vector representations of our images to compute similarities (the full details will be in our forthcoming JCAA paper). We are completely indebted to Douglas Duhaime and colleagues for clearly explicating and coding how this can be done.

---

![](8-98-1-SP.png)

Note:

disclaimer: These images are deliberately distant so that we can discuss the structure of what we're finding but not put the dead on display.

This is where we are at right now. After turning all of the images into vector representations, we use some statistical magic (t-sne and affinity clustering propagation) to understand the structure of visual similarity in the posts. The clustering algorithm identifies 'exemplar' images for each of the clusters that it finds.

---

<section data-background="8-97-1-SP.png">

Note:

We examine these exemplars - in our corpus, that's 84 images - by eye to work out what it is that the computer is 'seeing', comparing and correlating with our data mining of the text of posts themselves..

---

<section data-background="8-99-1-SP.png">

Note:

So far, it appears that the computer can discriminate skulls for sale by their arrangement on the shelf. Items for sale are arranged in ways that mimic 'popular' understandings of museology - glass cabinets with skulls arranged by size for instance.

Other clusters have been photographed square to the face, and largely fill the frame, and the associated language is largely of 'look at my collection' and 'look what i just gave away', perhaps signaling in other images that these materials could also be 'given away' - for a price. Another cluster positions the skulls such that they are turned slightly to the left; associated texts here clearly indicate something for sale.

This initial experiment does seem to support the idea that items for sale are displayed in ways that are discernible to the machine, and so, the machine can be taught to trawl other bodies of data for more evidence of the trade in human remains. The machine directs our attention to the framing of photographs, and the relationship of the human remains to other elements within the photograph. Exhibition design – rows of objects in cases on display – are recreated here. The interplay of foreground and background also seems to be important. Photos composed to show off a collection might also be subtly signaling that the item might also be for sale. These signals could be isolated, and used to train further iterations of a CNN, allowing a researcher to scale up their investigation. We intend to cross-reference this data with the network of followers and followed, to see how these visual clusters play out across networks of influence and on other platforms aside from Instagram.

---

### Training our own classifier

![](image-classifier.jpg)

[Build Your Own Classifier Tutorial](https://bonetrade.github.io/tutorials/tensorflow-for-poets/)

---

#### Find a path through image-space

![](mdlincoln-mechanical-kubler.png)


Note:
While this is an art-history application, I think we might be able to use a similar approach to find pathways of influence through images, if we start with images where we know that a followed/follower relationship exists. Matthew Lincoln, art historian & data scientist at the Getty


---

![](ryan-pastec.png)

- Ryan Baumann [Finding Near-Matches in the Rijksmuseum with Pastec](https://ryanfb.github.io/etc/2015/11/03/finding_near-matches_in_the_rijksmuseum_with_pastec.html)

Note:
Another way to find or determine influence- pastec looks for near copies, rather than visually similar. Which images are reposted, which occur across social networks? CNN could find this too, but this lets us zero in more quickly "Pastec is an open source index and search engine for image recognition." <- something like this might be very useful when trying to match eg polaroids to auction catalogues

---

### Ethically Troubling

<table>
  <tr>
    <th>![](faceall1.png)</th>
    <th>![](faceall2.png)</th>
  </tr>
</table>

---

## It's still early days.

Note:

for previous slide
Our funders are interested in us being able to identify descendent communities for the purposes of repatriation. Can we really do this? And if we are able, our experience in building classifiers so far just points out that what we believe about the images is easy to encode: if we say these are 'mowhawk', they become reified as mohawk. Finding visual tropes is one thing; saying that, beneath the tropes, this skull was a member of group x, y, z is I think a dangerous line to pursue. But is the good of repatriation worth the risk?

for current slide
This work is in its early stages. Despite being trained on a very generic corpus of images, Inception v3 seems to be a very powerful model for pulling out some of the visual rhetoric of display. If we train a model ourselves explicitly on archaeological materials, can we identify automatically at scale legal from illegal sales? ethical from non-ethical displays of remains? can we build an archaeo-crawler that would search these images, posts, and peoples out? would such a use be ethical? could one work out likely source peoples to whom these remains belong? given the use of computer vision for surveillance and social control, to what degree is our work dangerous and complicit? How do we ethically use computation to combat the trade?

---

### thank you

shawn.graham@carleton.ca

This research has been generously supported by the Social Sciences and Humanities Research Council of Canada

### [boonetrade.github.io](http://bonetrade.github.io)

for technical details, see our paper in <br> The Journal of Computer Applications in Archaeology, [DOI: 10.5334/jcaa.8](https://journal.caa-international.org/articles/10.5334/jcaa.8/) 

---
### Image Credits

- dramatization of Abraham Ulrikab - screenshot from CBC The Nature of Things, [Trapped in a Human Zoo](http://www.cbc.ca/natureofthings/episodes/trapped-in-a-human-zoo)
- screenshot of museum exhibiting skeletons - screenshot from CBC The Nature of Things, [Trapped in a Human Zoo](http://www.cbc.ca/natureofthings/episodes/trapped-in-a-human-zoo)
- Carter, GumGum gif [Neural Networks Made Easy](https://techcrunch.com/2017/04/13/neural-networks-made-easy/)
- sources for Instagram screenshots will not be shared in public

---
### Credits for Code & Demos & Screenshots 

- Finding Near-Matches in the Rijksmuseum with Pastec [Ryan Baumann](https://ryanfb.github.io/etc/2015/11/03/finding_near-matches_in_the_rijksmuseum_with_pastec.html)
- Identifying Similar Images with Tensorflow [Douglas Duhaime](http://douglasduhaime.com/posts/identifying-similar-images-with-tensorflow.html)
- Mechanical Kubler [Matthew Lincoln](https://github.com/mechanical-kubler/mechanical_kubler_generator)
- Machine Visions [Yannick Asogba](http://clome.info/work/machine-visions/)
- PixPlot visualization [Yale DH Lab](https://github.com/YaleDHLab/pix-plot)
- Tensorflow for Poets [Peter Warden/Google Codelabs](https://codelabs.developers.google.com/codelabs/tensorflow-for-poets/#0)

