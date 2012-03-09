---
layout: post
title: Shame, Licenses and DCO
category : development
tags : [licenses]
---
{% include JB/setup %}

## A licensing adventure ##

![Screen shot of the sample application](/assets/images/flow-screen-landscape.png)

> Discussed: Quick questions — How hard can it be? — Working code — Shame driven development — Simple attribution license — Commercial Non-attribution sub licensing — Managing contributions — Big honking disclaimer

This journey into licensing country started innocently enough when a student asked me (a quick question) if I knew of any good cover flow implementations they could use in their iOS projects. My answer was along the lines of dunno, those I've seen seemed like one-off experiments that probably have aged pretty badly. There probably are a lot of them around, and some of them might be good.

As most developers faced with the choice of googling for existing code/projects, reviewing them, converting them to arc - or whatever disrupting change that just hit your framework or language of choice - or simply doing it myself (how hard can it be?) I chose to start coding and the result is the [Flow Scroll](https://github.com/hugowetterberg/FlowScroll) project that triggered this post.

### Working code ###

I quickly got some working code by reducing the cover flow concept to images that rotate a variable number of degrees on the y-axis based on how far they are from the centre of a scroll view. What we don't get then is the stacking effect (which I never liked anyways, I think that it creates too big a disconnect between my finger movement and what's happening on the screen) but simply an image scroller that feels a bit more dynamic that a vanilla scroll view. Then it was just a matter of digging up [Apples sample code for creating reflection images](https://developer.apple.com/library/ios/#samplecode/Reflection/Introduction/Intro.html) and adapt it to attach the reflection to the image view as a sublayer instead of putting it into a separate UIImageView.

### Shame driven development ###

So, the code was in a "working" state. I immediately sent a message to [one of my former colleagues](https://github.com/simme): "Woot! Woot! I implemented a cover flow thingy!". The promt reply was - of course: show me the code. Showing stuff, to me, means make to make it public, unless there's a really good reason to keep the code private. So I did some minimal cleanup, an initial commit and then pushed it to github. This was when the shame started set in and I entered the "shame driven development" mode. I knew more or less what was missing to make this component really usable, most of it was written down in the readme. So why the hell had I published unfinished stuff that was more or less useless to other people? Once I realized that I was ashamed I really couldn't stop coding until pride at least overtook shame.

Fuelled by shame, shame, shame I finished the external api so that images could be added from arbitrary sources. Added a spinner to indicate that the image was in the queue. Ironed out bugs in the layouting and layer setup code. Wrote a delegate protocol that could react to clicks and supply images if something failed to load. And fleshed out the readme with a more decent introduction to how the component should be used. Suddenly my example went from proof of concept to something that actually was useful.

### Licensing ###

With the realization that you have something that could be useful to others comes the closely related realization that you'll have to decide on a license for your project. The license you choose is a matter of taste/ideological beliefs. Some people want a guarantee that the code and it's derivates remains free and untainted by any non-free (unclean) code and go the GPL route. I am not in that camp. Instead I prefer to prioritize the freedom of the people and projects who (hopefully) will use my code. What I do want is recognition for the work I've done: attribution.

#### The usual suspects and a juvenile delinquent ####

Having decided on the my ideological alignment the usual options are MIT/BSD license variants. Which all grants the user the right to do whatever their little twisted minds can come up with, as long as they attribute the code/functionality to me, stopping short of using my name as endorsement of their application. But every once in a while I re-research the license options that are available to me and this time I went outside the safe MIT/BSD choices and took a look at the relatively new [ICS license](http://en.wikipedia.org/wiki/ISC_license). The ICS license doesn't really change anything compared to the [Simplified BSD License](http://en.wikipedia.org/wiki/BSD_licenses#2-clause) but it's so concise that excepting the information about the copyright holder and the disclaimer it relly is just a single sentence:

> Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.

...or as I describe it in the Flow readme: "...it is short and easy to follow and boils down to this: use and modify freely, distribute for a fee or for free, I don't care, make money and be happy. BUT you must attribute me in all copies, that is: in your app and in the copied source code".

#### What's in it for me? ####

I think that we can all agree that the fame-levels resulting from implementing yet-another-cover-flow variant are pretty low; let's face it, cover flow was pretty old even when it first appeared in Mac OS X five years ago. I get a buzz from people using my code, or even just saying vaguely nice things about it, that's true. But I wanted an alternative for people that didn't want to pay me in soft cuddly social capital, but rather would show their appreciation with hard cold cash.

I was inspired by iOS development notables like [Matt Gemmel](http://mattgemmell.com/source/) who dual-license their code - providing a free attribution license, and a paid non-attribution license. I also looked at [Cocoanetics / Oliver Drobniks](http://www.cocoanetics.com/parts-store-terms-conditions/) terms and conditions to find out what terms and conditions should be in place for a commercial license non-attribution:

    Copyright (c) 2012, Hugo Wetterberg <hugo@wetterberg.nu>

    Non-attribution license for the HUWFlow component.

    This license permits use and modification of the offered source code for your own commercial or free apps. If you are using this code in a contracting project for a third party this party is also required to purchase a non-attribution license.

    You may not grant this access to third parties without the express written consent of Hugo Wetterberg. Nor shall you resell or rebrand this component to third parties as your own intellectual property.

    THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.

And no, eyeballing this licence doesn't give you a license to use the HUWFlow component, neither does that copy paste feature in your browser... get real.

To keep all this lean and easy I've decided to try out Gumroad for selling licenses: [https://gumroad.com/l/Wsa](https://gumroad.com/l/Wsa). That will be an interesting experiment in itself, so I  hope that someone actually buys a license so that I can see how it works ;)


#### How do we deal with contributors? ####

I wrote a piece of code, so far it's entirely within my rights to dictate how this piece of code should and should not be used. But how do we deal with contributions (as in pull requests, not as in donations)? I really don't want to lose the potential open source benefits, I put this on GitHub for a reason after all. But I need to establish a clear policy for contributions, a license for contributors. There is one über hostile way to go: the [CLA (Contributor License Agreement)](http://en.wikipedia.org/wiki/Contributor_License_Agreement); and there is the easier way: the [DCO (Developer Certificate of Origin)](http://elinux.org/Developer_Certificate_Of_Origin). See [Derek Jones enlightening article on the subject over at EllisLab](http://ellislab.com/blog/comments/contributor_license_agreements).

A CLA would require all *prospective* contributors to sign a contributor agreement before their contributions can be used. And any sane person would just tell me to go to hell if I tried to coax something like that out of them. But, DCO to the rescue. The DCO is the equivalent of an EULA for contributors, by contributing to the project and signing off on the patch or pull request the contributor accepts the DCO. This is the CONTRIBUTING.mdown file from the Flow project:

    Contributing
    ------------------------------

    Contributions require sign-off. The sign-off is a simple line at the end  of the commit message for the patch or pull request, which certifies that you wrote it or otherwise have the right to pass it on as an open-source patch. The rules are pretty simple: if you can certify the below:

        Developer’s Certificate of Origin
        =================================

        By making a contribution to this project, I certify that:

          (a) The contribution was created in whole or in part by me and I have the right to submit it under the open source license indicated in the file; or

          (b) The contribution is based upon previous work that, to the best of my knowledge, is covered under an appropriate open source license and I have the right under that license to submit that work with modifications, whether created in whole or in part by me, under the same open source license (unless I am permitted to submit under a different license), as indicated in the file; or

          (c) The contribution was provided directly to me by some other person who certified (a), (b) or (c) and I have not modified it.

          (d) I understand and agree that this project and the contribution are public and that a record of the contribution (including all personal information I submit with it, including my sign-off) is maintained indefinitely and may be redistributed consistent with this project or the open source license(s) involved.

          (e) I agree to the following terms and conditions:

            (1) Except for the license granted herein to the maintainer and recipients of software distributed by the maintainer, You reserve all right, title, and interest in and to your contributions.

            (2) Grant of Copyright License. Subject to the terms and conditions of this Agreement, You hereby grant to the maintainer and to recipients of software distributed by the maintainer a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable copyright license to reproduce, prepare derivative works of, publicly display, publicly perform, sublicense, and distribute your contributions and such derivative works.

            (3) Grant of Patent License. Subject to the terms and conditions of this Agreement, You hereby grant to the maintainer and to recipients of software distributed by the maintainer a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable (except as stated in this section) patent license to make, have made, use, offer to sell, sell, import, and otherwise transfer the Work, where such license applies only to those patent claims licensable by You that are necessarily infringed by your contribution(s) alone or by combination of your contribution(s) with the Work to which such contribution(s) was submitted. If any entity institutes patent litigation against You or any other entity (including a cross-claim or counterclaim in a lawsuit) alleging that your contribution, or the Work to which you have contributed, constitutes direct or contributory patent infringement, then any patent licenses granted to that entity under this Agreement for that contribution or Work shall terminate as of the date such litigation is filed.

            (4) You are not expected to provide support for your contributions, except to the extent You desire to provide support. You may provide support for free, for a fee, or not at all. Unless required by applicable law or agreed to in writing, You provide your Contributions on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied, including, without limitation, any warranties or conditions of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A PARTICULAR PURPOSE.

    then you just add a line saying

        Signed-off-by: Random J Developer <random@developer.example.org>

    When committing using the command line you can sign off using the --signoff or -s flag. This adds a Signed-off-by line by the committer at the end of the commit log message.

        git commit -s -m "Commit message"

The gist of this is that by submitting contributions to me *and* signing off the commit/patch the contributors certify that it is within their rights to submit the code. They also agree to grant me (not transfer) a copyright and patent license. Up until point (d) it is the standard Linux kernel DCO. This works well for them because the GPL license is pretty restrictive in itself, so no further clauses are needed. But as I'm using a more permissive license I have taken parts of the [Apache CLA](http://www.apache.org/licenses/icla.pdf) and added as terms and conditions under point (e).

The disclaimer
--------------

This would be the perfect moment to point out that what I know about law could easily fit into a very small thimble. But it looks reasonable enough doesn't it? To quote Derek Jones disclaimer:

> The content in this article is neither legal advice nor a legally binding interpretation of the licenses discussed, including those distributed with EllisLab products. We are sharing our opinions, thoughts and conclusions which we hope are helpful and spark meaningful discussion. You should consult an attorney with questions regarding your specific legal needs and the terms or interpretation of any software license.

If you mentally replace "EllisLab" with "my" the same disclaimer goes for what I've written here. Flow is obviously not a very large project. It was an opportunity for me to explore both technical and legal issues surrounding this type of components. If a hypothetical lawyer would start sending emails about me not being able to restrict my hypothetical contributors in this way it won't be a big issue to me. I'll just go: "Sure! Do you want the 25 bucks I have earned on this too? Buy yourself a coffee or two, my treat!". If you will depend on a project for your livelihood, or a substantial part of it, and you're considering a similar license model you should get yourself a lawyer that makes sure that everything checks out.
