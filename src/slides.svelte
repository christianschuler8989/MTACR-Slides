<script lang="ts">
	import { Presentation, Slide, Notes, Step } from '@components'
	import Layout from './layout.svelte'
</script>

<!-- Typical Errors
	
	"Uncaught TypeError: slidesInChapter[0] is undefined" and layout elements missing.
	→ This can happen if a chapter is defined but has no slides.

-->

<Presentation>	
	<script>
		// information about this presentation 
		const author = "Christian Schuler, Tramy Thi Tran, Deepesha Saurty, <br>Anran Wang, Raman Ahmad, Seid Muhie Yimam"; 
		const authorshort = "Schuler, Tran, Saurty, Wang, Ahmad, Yimam"; 
		const title = "TextAsCorpusRep";
		const subtitle = "Multilingual Text As Corpus Repository for Machine Translation of Low-Resource Languages";
		const department = "DDLitLab Student's Project"; 
		const university = "University of Hamburg"; 
		var currentChapterName="";
		var currentChapterNumber=0;
		var chapterNames=[];
		var toc = false;  // whether toc is to be generated
		// data structure: [chapter number, chapter name, slideID]
		var presentationData = []; 
		function newChapter(chapterName){
			currentChapterName=chapterName; 
			currentChapterNumber++;
			chapterNames.push(chapterName);
		}
		// called when new slide is created
		var page=0; 
		function newPage(){
			page++; //note that page n has index n-1
			presentationData.push({chapternr: currentChapterNumber, chapter:currentChapterName,pagenr:page});
		}
	</script>

	<!-- title page -->
	<Slide><Layout>
		<div class="m-16 flex h-[25vh] w-[90vw] bg-[var(--themecolor)] text-white items-center justify-center gap-[100px]">
			<div>
				<div class="text-[6vh]">
					<span id="mytitle"> </span>
				</div>
				<br>
				<div class="text-[4vh]">
					<span id="mysubtitle"> </span>
				</div>
			</div>
		</div>
		<br>
		<div> 
			<span id="myname"></span>
		</div>
		<br>
		<div class="text-[3vh]"> 
			<span id="myuni"></span>
		</div>
		<div class="text-[3.5vh]"> 
			<br>
			<span id="mydate"></span>
		</div>
		<br>
		<!-- <div class="flex items-center justify-center">
			<img class="h-[15vh] align-middle" src="title-logo.png" alt="tum logo">
		</div> -->
		<!-- fill in the data for this presentation  -->
		<script> 
			document.getElementById("mytitle").innerHTML=title;
			document.getElementById("mysubtitle").innerHTML=subtitle;
			document.getElementById("myname").innerHTML=author;
			document.getElementById("myuni").innerHTML=department+"<br>"+university;
			let today = new Date(); 
			document.getElementById("mydate").innerHTML=today.toISOString().split('T')[0]; 
		</script>
	</Layout></Slide>
	<!-- TOC -->
	<!-- <Slide>
		<script>
			toc=false; // decides whether to generate table of content page
		</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide> -->
	
	<!-- intro -->
	<script>newChapter("Introduction")</script>
	<Slide>
		<Layout>
			<titlebar>
				Project Team
			</titlebar>
			<mybody>
				<div class="grid" style="grid-template-columns: auto auto auto auto auto auto; mx-auto my-auto;">
					<!-- Names -->
					

					<div class="flex w-[16vw] items-center justify-center gap-[5px] text-[3vh]">
						Christian Schuler
					</div>
					<div class="flex w-[16vw] items-center justify-center gap-[10px] text-[3vh]">
						Tramy Thi Tran
					</div>
					<div class="flex w-[16vw] items-center justify-center gap-[10px] text-[3vh]">
						Deepesha Saurty
					</div>
					<div class="flex w-[16vw] items-center justify-center gap-[10px] text-[3vh]">
						Anran Wang
					</div>
					<div class="flex w-[16vw] items-center justify-center gap-[10px] text-[3vh]">
						Raman Ahmad
					</div>
					<div class="flex w-[16vw] items-center justify-center gap-[10px] text-[3vh]">
						Seid Muhie Yimam
					</div>

					<!-- Images -->
					<figure class="h-[60vh] w-[15vw] float-left mx-auto my-auto">
						<a href="https://christianschuler8989.github.io/">
							<img src="Christian_Schuler_08_Energydrink.jpg" alt="christian" class="h-[40vh]">
							<figcaption class="text-[2.3vh]">
								Master student in computer science at University of Hamburg.
							</figcaption>
							<figcaption class="text-[1.3vh]">
								With a passion for languages and colors, he aims to do a PhD. <br>Additionally, he eats more pizza in one year than any of you in your lifetime!
							</figcaption>
						</a>
					</figure>
					<figure class="h-[60vh] w-[15vw] float-left mx-auto my-auto">
						<a href="LINK_FOR_TANIA_HERE">
							<img src="DDLitLab-TextAsCorpusRep-Myyyy2.jpeg" alt="myy" class="h-[40vh]">
							<figcaption class="text-[2.3vh]">
								Bachelor student in something like computer science at University of Hamburg.
							</figcaption>
							<figcaption class="text-[1.3vh]">
								She is not simply the head of our HR-department, she IS the entire department! XD #bestProjectCoordinatorInTown
							</figcaption>
						</a>
					</figure>
					<figure class="h-[60vh] w-[15vw] float-left mx-auto my-auto">
						<a href="LINK_FOR_TANIA_HERE">
							<img src="DDLitLab-TextAsCorpusRep-Tania2.jpg" alt="tania" class="h-[40vh]">
							<figcaption class="text-[2.3vh]">
								Bachelor student in computer science at University of Hamburg.
							</figcaption>
							<figcaption class="text-[1.3vh]">
								By now she went down the rabbit hole of science so much, that people actually heard her say "Algorithms are fun!"
							</figcaption>
						</a>
					</figure>
					<figure class="h-[60vh] w-[15vw] float-left mx-auto my-auto">
						<a href="https://anranw.github.io/">
							<img src="Anran_Wang_01.png" alt="anran" class="h-[40vh]">
							<figcaption class="text-[2.3vh]">
								Master student in computer science at Technical University Munich.
							</figcaption>
							<figcaption class="text-[1.3vh]">
								She is so awesome, that she did not start looking for a PhD position like most mortal beings do- the PhD position came falling out of the sky and had to apply to her first!
							</figcaption>
						</a>
					</figure>
					<figure class="h-[60vh] w-[15vw] float-left mx-auto my-auto">
						<a href="https://ramanahmad.github.io/">
							<img src="Raman_Ahmad_01.png" alt="raman" class="h-[40vh]">
							<figcaption class="text-[2.3vh]">
								Bachelor student in computer science at Hochschule für Angewandte Wissenschaften in Hamburg.
							</figcaption>
							<figcaption class="text-[1.3vh]">
								He is currently exploring various ways to advance the low-resource language Kurdish with a focus on the Kobani dialect.
							</figcaption>
						</a>
					</figure>
					<figure class="h-[60vh] w-[15vw] float-left mx-auto my-auto">
						<a href="https://seyyaw.github.io/">
							<img src="DDLitLab-TextAsCorpusRep-Mentor.jpeg" alt="seid" class="h-[40vh]">
							<figcaption class="text-[2.3vh]">
								Technical Lead at HCDS and Research Associate at Language Technology Group in Hamburg.
							</figcaption>
						</a>
						<figcaption class="text-[1.3vh]">
							He researches low-resource languages, in particular related to the Amharic language, while he uses his spare time to mentor and supervise groups of students like noone else could! :D
						</figcaption>
					</figure>
					
					<!-- Logos -->
					<figure class="flex h-[10vh] w-[15vw] items-center justify-center mx-auto my-auto">
						<img src="uhh-logo.png" alt="uhh-logo" class="h-[7vh]">
					</figure>
					<figure class="flex h-[10vh] w-[15vw] items-center justify-center mx-auto my-auto">
						<img src="uhh-logo.png" alt="uhh-logo" class="h-[7vh]">
					</figure>
					<figure class="flex h-[10vh] w-[15vw] items-center justify-center mx-auto my-auto">
						<img src="uhh-logo.png" alt="uhh-logo" class="h-[7vh]">
					</figure>
					<figure class="flex h-[10vh] w-[15vw] items-center justify-center mx-auto my-auto">
						<img src="tum-logo.png" alt="tum-logo" class="h-[7vh]">
					</figure>
					<figure class="flex h-[10vh] w-[15vw] items-center justify-center mx-auto my-auto">
						<img src="haw-logo.png" alt="haw-logo" class="h-[7vh]">
					</figure>
					<figure class="flex h-[10vh] w-[15vw] items-center justify-center mx-auto my-auto">
						<img src="uhh-logo.png" alt="uhh-logo" class="h-[7vh]">
					</figure>
					
				</div>
			</mybody>
		</Layout>
	</Slide>

	<Slide><Layout>
		<titlebar > Our Idea </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="title-banner.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script>newChapter("Motivation");</script>
	<Slide><Layout>
		<titlebar > Translation Systems (Here Google Translate) Failing Languages  </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="CRAMT-Tool-MotivationSimpleMore.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Lack of Standardization </titlebar>
		<mybody>
			<figure>
				<table>
					<tr>
						<th>Dialect Group</th>
						<th>#Var</th>
						<th>#ISO Codes</th>
						<th>#Wiki (Articles)</th>
					</tr>
					<tr>
						<td>Central Kurdish</td>
						<td>13</td>
						<td>2</td>
						<td>53,856</td>
					</tr>
					<tr>
						<td>Northern Kurdish</td>
						<td>28</td>
						<td>1</td>
						<td>75,358</td>
					</tr>
					<tr>
						<td>Southern Kurdish</td>
						<td>13</td>
						<td>1</td>
						<td>0</td>
					</tr>
					<tr>
						<td>Zazaki</td>
						<td>10</td>
						<td>3</td>
						<td>41,811</td>
					</tr>
					<tr>
						<td>Gorani</td>
						<td>13</td>
						<td>4</td>
						<td>0</td>
					</tr>
				  </table>
				<figcaption class="text-[3.5vh]">
					Number of language varieties (#Var) and <br> corresponding ISO-Codes (#ISO) according to Glottolog [1], <br> number of wikipedia articles (#Wiki) according to Wikimedia [2].
				</figcaption>
				<p class="text-[2vh]">
					<br>
					[1] http://glottolog.org
					<br>
					[2] https://meta.wikimedia.org/wiki/List_of_Wikipedias_by_language_group
				</p>
			</figure>
			
		</mybody>
	</Layout>
	<Notes>
		Harald Hammarström, Robert Forkel, Martin Haspelmath, and Sebastian Bank. 2023. Glot- tolog 4.8. (Available online at http://glottolog.org, Accessed on 2024-03-06.).
		Wikimedia. 2024. List of Wikipedias by language group - Meta — meta.wikimedia.org. https://meta.wikimedia.org/wiki/List_of_Wikipedias_by_language_group. [Accessed 06-03-2024].
	</Notes></Slide>

	<script>newChapter("Our Languages")</script>
	<Slide><Layout>
		<titlebar>Vietnamese </titlebar>
		<mybody>
			
			<div class="backgrounds bg-cover bg-center" style="background-image: url('Vietnam-Background.png'); margin-top:4.3rem; margin-bottom: 2rem;">
				<div class="grid" style="grid-template-columns: 2fr 1fr; mx-auto my-auto;">
					<div>
						<p class="text-3xl font-bold mt-4 ml-12 text-left">Name:</p>
					<ul class="d">
						<li>Vietnamese (Tiếng Việt)</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Vietnam: </span>
						Country in Southeast Asia
					</p>
					<ul class="d">
						<li>Prior to the alphabet reform, Vietnam used Chinese
							characters (Chữ Nôm)</li>
						<li>When Vietnam was conquered by the French, the Latin alphabet (Chữ Quốc Ngữ) systematically replaced the Chinese characters as the written language for everybody 
							<br> -&gt greatly increased literacy in Vietnam</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Vietnamese: </span>
						Three main dialect regions
					</p>
					<ul class="d">
						<li>More than 80 million native speakers</li>
						<li>Various dialects, generally mutually intelligible</li>
						<li>Vocabulary influenced by Chinese and French</li>
					</ul>
					</div>
					<div class="flex justify-center items-center">
						<img src="Vietnam-Wikipedia-Position.png" alt="Vietnam Position" class="h-[60vh] w-auto mr-16">
					</div>
				</div>
				
			</div>
			
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar>Kurdish </titlebar>
		<mybody>
			<div class="backgrounds bg-cover bg-center" style="background-image: url('Kurdistan-Background.png'); margin-top:4.3rem; margin-bottom: 2rem;">
				<div class="grid" style="grid-template-columns: 2fr 1fr; mx-auto my-auto;">
					<div>
						<p class="text-3xl font-bold mt-4 ml-12 text-left">Name:</p>
					<ul class="d">
						<li>Kurdish (Kurdî)</li>
						<li>Kurdish -&gt Kurmanji -&gt Southwestern -&gt Kobani</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Kurdistan: </span>
						Not being an officially recognized nation
					</p>
					<ul class="d">
						<li>Scene of armed struggles since First World War</li>
						<li>No government that organizes or funds language research</li>
						<li>Population separated over nations and language spheres</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Kurdish: </span>
						Made up of a vast dialect continuum
					</p>
					<ul class="d">
						<li>Approximately 25 million speakers</li>
						<li>Sorani (Central Kurdish) ~7 million Kurds</li>
						<li>Kurmanji (Northern Kurdish) ~15-20 million Kurds</li>
						<li>For a long time illegal to read & write</li>
					</ul>
					</div>
					<div class="flex justify-center items-center">
						<img src="Kurdistan-Wikipedia-Position.png" alt="Kurdistan Position" class="h-[60vh] w-auto mr-16">
					</div>
				</div>
				
			</div>
			
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar>Mauritian Creole </titlebar>
		<mybody>
			<div class="backgrounds bg-cover bg-center" style="background-image: url('Mauritius-Background.png'); margin-top:4.3rem; margin-bottom: 2rem;">
				<div class="grid" style="grid-template-columns: 2fr 1fr; mx-auto my-auto;">
					<div>
						<p class="text-3xl font-bold mt-4 ml-12 text-left">Name:</p>
					<ul class="d">
						<li>Mauritian Creole or Morisien (formerly Morisyen)</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Mauritius: </span>
						An island nation and popular tourist spot
					</p>
					<ul class="d">
						<li>Morisien is a young language influenced by many others</li>
						<li>Only recently formalized grammar and spelling</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Morisien: </span>
						A relatively small language community
					</p>
					<ul class="d">
						<li>Approximately 1.3 million speakers</li>
						<li>French-based, with some English loan-words</li>
						<li>Different spellings and grammar rules</li>
					</ul>
					</div>
					<div class="flex justify-center items-center">
						<img src="Mauritius-Wikipedia-Position.png" alt="Mauritius Position" class="h-[60vh] w-auto mr-28">
					</div>
				</div>
				
			</div>
			
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>


	<Slide><Layout>
		<titlebar>Chinese </titlebar>
		<mybody>
			<div class="backgrounds bg-cover bg-center" style="background-image: url('China-Background.png'); margin-top:4.3rem; margin-bottom: 2rem;">
				<div class="grid" style="grid-template-columns: 2fr 1fr; mx-auto my-auto;">
					<div>
						<p class="text-3xl font-bold mt-4 ml-12 text-left">Name:</p>
					<ul class="d">
						<li>Chinese (simplified) (汉语)</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">China: </span>
						Country in East Asia exceeding 1.4 billion inhabitants
					</p>
					<ul class="d">
						<li>Chinese is classified into more than 10 dialect groups</li>
						<li>Many of which are mutually unintelligible</li>
					</ul>
					<p class="text-3xl mt-4 ml-12 text-left">
						<span class="font-bold">Chinese: </span>
						A standardized writing system used for all variants
					</p>
					<ul class="d">
						<li>Many low-resource variants, not even properly classified</li>
						<li>Standard Chinese though, provides lots of resources & tools</li>
						<li>Proposed as alternative to English-centric NLP research</li>
					</ul>
					</div>
					<div class="flex justify-center items-center">
						<img src="China-Wikipedia-Position.png" alt="China Position" class="h-[60vh] w-auto mr-28">
					</div>
				</div>
				
			</div>
			
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Related Work"); </script>
	<Slide><Layout>
		<titlebar > Collecting Text Data </titlebar>
		<mybody>
			<!-- <div class="flex items-center justify-center">
				<img class="h-[70vh] align-middle" src="CRAMT-Tool-TextAlignmentsOverviewMulti.png" alt="tum logo">
			</div> -->
			TODO: Selenium Web Crawling Image
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Bridging the Language Gap </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[70vh] align-middle" src="CRAMT-Tool-TextAlignmentsOverviewMulti.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Use of Pivot Languages </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[70vh] align-middle" src="CRAMT-Tool-TextAlignments.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Bilingual Lexicon Induction (TODO) </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="title-banner.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Language Ambiguities I </titlebar>
		<mybody>
			<figure class="h-[30vh] w-[95vw] float-left mx-auto my-auto">
				<img src="CRAMT-Tool-WordAlignmentExample.png" alt="ambiguities1" class="h-[30vh]">
				<figcaption class="w-[93vw]">
					Finding new word alignments by traversing multiple cross-lingual alignments and assuming these relations to be transitive.
				</figcaption>
			</figure>
			<!-- <div class="flex items-center justify-center">
				<img class="h-[30vh] w-[95vw] align-middle" src="CRAMT-Tool-WordAlignmentExample.png" alt="tum logo">
			</div> -->
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Language Ambiguities II </titlebar>
		<mybody>
			<figure class="h-[80vh] w-[95vw] float-left mx-auto my-auto">
				<img src="CRAMT-Tool-WordAlignmentLimitation.png" alt="ambiguities2" class="h-[70vh]">
				<figcaption class="w-[93vw] text-[4vh]">
					The word ambiguity during translation of the German Grün into the English green resulting in additional translation candidates.
				</figcaption>
			</figure>

			<!-- <div class="flex items-center justify-center">
				<img class="h-[70vh] w-[95vw] align-middle" src="CRAMT-Tool-WordAlignmentLimitation.png" alt="tum logo">
			</div> -->
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Language Ambiguities III </titlebar>
		<mybody>
			<figure class="h-[80vh] w-[95vw] float-left mx-auto my-auto">
				<img src="CRAMT-Tool-WordAlignmentLimitationExample.png" alt="ambiguities1" class="h-[70vh]">
				<figcaption class="w-[93vw] text-[4vh]">
					Continuing on ambiguous translations (red) instead of aggregating to the most likely candidate (green) can enrich a dataset with additional labels across languages (blue).
				</figcaption>
			</figure>

			<!-- <div class="flex items-center justify-center">
				<img class="h-[70vh] w-[95vw] align-middle" src="CRAMT-Tool-WordAlignmentLimitationExample.png" alt="tum logo">
			</div> -->
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Collecting Multilingual Text Data </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto; mx-auto my-auto;">
				<div class="text-[5vh] p-5">
					Translating from English
				</div>
				<div class="text-[5vh] p-5">
					Monolingual Descriptions
				</div>
				<figure class="h-[25vh] w-[30vw] mx-auto my-auto">
					<a href="https://ai.meta.com/research/no-language-left-behind/">
						<img src="nllb-logo.png" alt="NLLB Logo" class="w-[20vw] h-[20vh] align-middle">
						<!-- Source: https://wandb.ai/telidavies/ml-news/reports/Meta-Releases-NLLB-200-New-Open-Source-Model-Able-To-Translate-200-Languages--VmlldzoyMjc4NzIz -->
					</a>
				</figure>
				<figure class="h-[25vh] w-[30vw] mx-auto my-auto">
					<a href="https://paperswithcode.com/dataset/flickr30k">
						<img src="flickr30k-logo.png" alt="Flickr30k Logo" class="w-[30vw] h-[20vh] align-middle">
						<!-- Source: https://paperswithcode.com/dataset/flickr30k -->
					</a>
				</figure>
				<div class="text-[3vh]">
					No Language Left Behind (NLLB) is a first-of-its-kind, 
					AI breakthrough project that open-sources models capable of delivering evaluated, 
					high-quality translations directly between 200 languages—
					including low-resource languages like Asturian, Luganda, Urdu and more. 
					<br><br>
					It aims to give people the opportunity to access and 
					share web content in their native language, 
					and communicate with anyone, anywhere, regardless of their language preferences.
				</div>
				<div class="text-[3vh]">
					The Flickr30k dataset contains 31,000 images collected from Flickr, 
					together with 5 reference sentences provided by human annotators.
					<br><br>
					Has already been extended to German, French, Czech, Chinese, and Ukrainian
				</div>
			</div>
			
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Design \& Development"); </script>
	<Slide><Layout>
		<titlebar > Overview of CRAMT </titlebar>
		<mybody>
			<figure class="h-[80vh] w-[70vw]">
				<img src="CRAMT-Tool-OverviewSimpleSlick.png" alt="ambiguities1" class="mx-auto">
				<figcaption>
					Overview of the CRAMT toolkit. User inputs in blue, main processing steps in yellow and resulting artifacts in green.
				</figcaption>
			</figure>

			<!-- <div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="CRAMT-Tool-OverviewSimpleSlick.png" alt="tum logo">
			</div> -->
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<!-- <script> newChapter("Used Tools"); </script> -->
	<Slide><Layout>
		<titlebar > GlotLID (TODO) </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="title-banner.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>
	
	<Slide><Layout>
		<titlebar > Potato (TODO) </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="title-banner.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Data Quality"); </script>
	<Slide><Layout>
		<titlebar > Annotation via Anchor Items </titlebar>
		<mybody>
			<div class="flex items-center justify-center">
				<img class="h-[75vh] align-middle" src="CRAMT-Tool-AnnotationQuality.png" alt="tum logo">
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Data Collected (NLLB-01)</titlebar>
		<mybody>
			<ul class="a" >
				<li>English (Original Text)</li>
				<li>"Lillian Diana Gish (October 14, 1893 – February 27, 1993) was an American actress, director and screenwriter."</li>
				<br>
				<li>German (MT via GoogleTranslate and ChatGPT)</li>
				<li>"Lillian Diana Gish (14. Oktober 1893 – 27. Februar 1993) war eine US-amerikanische Schauspielerin, Regisseurin und Drehbuchautorin."</li><!--GoogleTranslate-->
				<li>"Lillian Diana Gish (14. Oktober 1893 – 27. Februar 1993) war eine amerikanische Schauspielerin, Regisseurin und Drehbuchautorin."</li><!--ChatGPT-->
				<br>
				<li>Morisien 
				<li>"Lillian Diana Gish (inn ne 14 Oktob 1893 – inn mor 27 Fevrie 1993) li ti enn akter, enn realizater ek enn senaris Amerikenn."
				<li>"Lillian Diana Gish (14 Oktob 1893 - 27 Fevriye 1993) ti enn aktris, realizatris ek senarist amerikenn."</li>
				<br>
				<li>"Vietnamese"</li>
				<li>"Lillian Diana Gish, sinh ngày 14 tháng 10 năm 1893 và mất ngày 27 tháng 2 năm 1993, là một nữ diễn viên, đạo diễn và biên kịch người Mỹ."</li>
				<li>"Lillian Diana Gish (14/10/1893 – 27/2/1993) là một nữ diễn viên, đạo diễn, biên kịch người Mỹ."</li>
				<li>"Lillian Diana Gish (14/10/1893 – 27/02/1993) là một nữ diễn viên, đạo diễn và nhà biên kịch người Mỹ."</li>
				<br>
				<li>"Kobani"
				<li>"Lillian Diana Gish (14'î mehê 10'an 1893 - 27'î mehê didîyan 1993) lîstikvan, derhêner û sînaronivîseke Emrîkî bû."</li>
				<li>"Lilian Diana Gish (14î meha dehan, 1893 - 27î meha didiyan , 1993) lîstikvan, derhêner, û senarîsteke Emrîkî bû."</li>
				<br>
				<li>Chinese</li>
				<li>"莉莲·戴安娜·吉什（1893年10月14日-1993年2月27日），美国女演员、导演和编剧。"</li>
				<li>"莉莲·戴安娜·吉什（1893年10月14日－1993年2月27日）是一位美国女演员、导演和编剧。"</li>
				<li>"莉莉安·黛安娜·吉许（1893年十月十四日-1993年二月27日）是一个美国演员，导演和编剧。"</li>
			</ul>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Data Collected (NLLB-02)</titlebar>
		<mybody>
			<ul class="a" >
				<li>English (Original Text)</li>
				<li>"The seventeen-year-old Lillian traveled to Shawnee, Oklahoma, where James's brother Alfred Grant Gish and his wife, Maude, lived."</li>
				<br>
				<li>German (MT via GoogleTranslate and ChatGPT)</li>
				<li>"Die siebzehnjährige Lillian reiste nach Shawnee, Oklahoma, wo James‘ Bruder Alfred Grant Gish und seine Frau Maude lebten."</li><!--GoogleTranslate-->
				<li>"Die siebzehnjährige Lillian reiste nach Shawnee, Oklahoma, wo James' Bruder Alfred Grant Gish und seine Frau, Maude, lebten."</li><!--ChatGPT-->
				<br>
				<li>Morisien 
				<li>"Laz diset-an, Lillian ti al rest dan lavil Shawnee an Oklahoma (Etazini), kot frer so papa James, ki apele Alfred Grant Gish ek so madam, Maude."
				<li>"Lillian, ki ena diset an, ti al Shawnee, dan Oklahoma, kot frer James, Alfred Grant Gish ek so madam, Maude ti viv."</li>
				<br>
				<li>"Vietnamese"</li>
				<li>"Ở tuổi mười bảy, Lillian đến Shawnee, Oklahoma, nơi anh trai của James, Alfred Grant Gish và vợ Maude sinh sống."</li>
				<li>"Lillian, khi đó 17 tuổi, đã đến thành phố Shawnee thuộc tiểu bang Oklahoma, nơi anh trai của James là Alfred Grant Gish và vợ của ông ấy sinh sống."</li>
				<li>"Cô nàng Lillian mười bảy tuổi đã đến Shawnee, Oklahoma, tại đây có người anh trai của James là Alfred Grant Gish và vợ Maude sinh sống."</li>
				<br>
				<li>"Kobani"
				<li>"Lillian 17-salî çû Shawnee, Oklahoma, cihê ku birayê James Alfred Grant Gish û jina wî, Maude, lê dijîyan."</li>
				<li>"Lilliana hevde salîn çû Shawnee, Oklahoma, cê ku birê James Alfred Grant Gish û jina xwe lê dijiyan."</li>
				<br>
				<li>Chinese</li>
				<li>"17岁的莉莲前往俄克拉何马州的肖尼市，詹姆斯的哥哥阿尔弗雷德·格兰特·吉什和他的妻子莫德就住在那里。"</li>
				<li>"17岁的莉莲前往俄克拉荷马州的肖尼市，詹姆斯的哥哥Alfred Grant Gish和他的妻子Maude住在那里。"</li>
				<li>"17岁的莉莉安去了奥克拉荷马州的肖尼，在那里住过詹姆斯的兄弟阿尔弗雷德·格兰特·吉许和他的妻子莫德。"</li>
			</ul>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Data Collected (Flikr30k-01)</titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto; mx-auto my-auto;">
				<img src="13651137.jpg" alt="Flikr30k Number 80" class="h-[75vh]">
				<ul class="b" >
					<li>Kobani</li>
					<li>"mêrkek bi kombrêsê erdê xerab dikê"</li>
					<br>
					<li>Morisien</li>
					<li>"enn missier p craze simin avec so machine craz roche"</li>
					<br>
					<li>Vietnamese</li>
					<li>"Một công nhân xây dựng đang làm việc với một búa khoan."</li>
					<li>"Anh ấy đang phá dỡ đường"</li>
					<br>
					<li>Chinese</li>
					<li>"一名工人正在拆除房屋前面的水泥路面"</li>
					<br>
				</ul>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Data Collected (Flikr30k-02)</titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto; mx-auto my-auto;">
				<img src="10815824.jpg" alt="Flikr30k Number 16" class="w-[50vw]">
				<ul class="b" >
					<li>Kobani</li>
					<li>"Qîzkek û mêrekî li baxçakî ne, li ber qîzikê hespek hê û li paş merik jî yek hê. Qîzik û hespî xwe li ber êr in."</li>
					<br>
					<li>Vietnamese</li>
					<li>"Cô gái đang chăn ngựa"</li>
					<li>"Trong trang là hình ảnh cô bé đang dắt 1 chú ngựa và phía đằng xa có lẻ là 1 huấn luyện viên của cô ấy thì phải."</li>
					<li>"Cô gái mặc áo đen đang đứng cầm dây cương ngựa, cả hai đứng bên cạnh một bếp lữa."</li>
					<br>
					<li>Chinese</li>
					<li>"因为年轻女士牵着马站在火堆前"</li>
					<br>
				</ul>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Current State"); </script>

	<Slide><Layout>
		<titlebar > Collected Data </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto; mx-auto my-auto;">
				<Step fadeRight><img src="mtacr-2024-april.png" alt="Data Kob Mfe" class="w-[45vw] h-[40vh]"></Step>
				<Step fadeRight><img src="mtacr-2024-april-targets.png" alt="Data Kob Mfe" class="w-[45vw] h-[40vh]"></Step>
				<Step fadeDown><img src="mtacr-2024-april-noeng.png" alt="Data Kob Mfe" class="w-[45vw] h-[40vh]"></Step>
				<Step fadeDown><img src="mtacr-2024-april-all.png" alt="Data Kob Mfe" class="w-[45vw] h-[40vh]"></Step>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Insights Gained </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto auto; mx-auto my-auto;">
				<!-- Images -->
				Doing this kind of work is [chết tiệt] hard!
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Introducing CRAMT - A Participatory Research Approach</titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto; mx-auto my-auto;">
				<!-- Images -->
				<div class="h-[75vh] w-[45vw]">
				<ul class="b" >
					<li>To enable others to do what we did
						<ul class="b" >
							<li>less tech-savvy? </li>
							<li>new to NLP? </li>
							<li>no idea where to start? </li>
						</ul>
				</ul>
				</div>
				<div class="h-[75vh] w-[45vw]">
					<iframe src="2024-CRAMT_Poster_Expo-Schuler_Tran_Saurty_Wang_Ahmad_Yimam.pdf#page=1&zoom=13" frameBorder="0" scrolling="auto" height="100%" width="100%" title="ESSV Publication"></iframe>
				</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > CRAMT at Workshop on Building and Using Comparable Corpora (LREC-COLING) </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto; mx-auto my-auto;">
				<!-- Images -->
				<p>
					Close, but no cigar!<br>
					Additional to the reviews we received very encouraging words though:<br><br>	
				</p>
				
				<p>
					The selection process was very competitive. 
					Due to time and space limitations, we could only choose a limited number of the submitted papers 
					to appear on the program. Nonetheless, I still hope you can attend the conference. <br>
					Additionally, <mark> given the interest found in your project, we encourage you 
					to submit an updated version of your paper next year.</mark><br><br>
				</p>

				<p>
					We are happy that you found the reviewers' comments useful.  
					As mentioned in the specific word added to the notification message, 
					<mark>we hope you can submit an updated paper next year!</mark> 
				</p>
				
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > CRAMT at EXPO-2024 </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto auto; mx-auto my-auto;">
				<!-- Images -->
				<figure class="h-[65vh] w-[40vw] float-left mx-auto my-auto">
					<img src="event-2024-EXPO-Poster.jpg" alt="CRAMT EXPO" class="h-[65vh]">
					<figcaption class="text-[3.3vh]">
						Poster presentation to faculty, students, pupils.
					</figcaption>
				</figure>
				<figure class="h-[65vh] w-[52vw] float-left mx-auto my-auto">
					<img src="event-2024-EXPO-CRAMT-SecondPlace-TaniaRamanChristianMyyAnran.JPG" alt="CRAMT award" class="h-[65vh]">
					<figcaption class="text-[3.3vh]">
						CRAMT was awarded second place.
					</figcaption>
				</figure>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Future Work"); </script>
	<Slide><Layout>
		<titlebar > Language Data waiting to be collected </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto auto; mx-auto my-auto;">
				<!-- Images -->
				<figure class="h-[35vh] w-[30vw] float-left mx-auto my-auto">
					<img src="Kurmanjî-wordcloud.png" alt="kurmanji" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						Kurmanji
					</figcaption>
				</figure>
				<figure class="h-[35vh] w-[30vw] float-left mx-auto my-auto">
					<img src="Morisien-wordcloud.png" alt="morisien" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						Morisien
					</figcaption>
				</figure>
				<figure class="h-[35vh] w-[30vw] float-left mx-auto my-auto">
					<img src="Vietnamese-wordcloud.png" alt="vietnamese" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						Vietnamese
					</figcaption>
				</figure>

				<figure class="h-[35vh] w-[30vw] float-left mx-auto my-auto">
					<img src="Chinese-wordcloud.png" alt="chinese" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						Chinese
					</figcaption>
				</figure>
				<figure class="h-[35vh] w-[30vw] float-left mx-auto my-auto">
					<img src="German-wordcloud.png" alt="german" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						German
					</figcaption>
				</figure>
				<figure class="h-[35vh] w-[30vw] float-left mx-auto my-auto">
					<img src="English-wordcloud.png" alt="english" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						English
					</figcaption>
				</figure>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Let There Be Cake ! </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto; mx-auto my-auto;">
				<!-- Images -->
				<figure class="h-[80vh] float-left mx-auto my-auto">
					<img src="Christian_Schuler-EXPO_2024_Cake.JPG" alt="CAKE" class="h-[75vh]">
					<figcaption class="text-[3.3vh]">
						Conceptualization of future conference attendence.
					</figcaption>
				</figure>
				<div class="w-[50vw]">
					<ul class="b" >
						<li>1. CRAMT tool demo-paper at ACL or EMNLP(?)</li>
						<br>
						<li>2. CRAMT tool research-paper once we have</li>
							<ul class="b" >
								<li>some more results and </li>
								<li>the time to do more evaluations</li>
							</ul>
						<br>
						<li>3. MTACR corpus research-paper.</li>
					</ul>
				</div>
				
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Conclusion"); </script>
	<Slide><Layout>
		<titlebar > Main Project: TextAsCorpusRep </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto; mx-auto my-auto;">
				<a href="https://github.com/Low-ResourceDialectology/TextAsCorpusRep">
					<img src="TextAsCorpusRep-Auxiliary-Logo.png" alt="MTACR Logo" class="w-[90vw]">
					<figcaption class="text-[2.3vh]">
						Multilingual Text As Corpus Repository for Machine Translation of Low-Resource Language
					</figcaption>
				</a>
				<ul class="b" >
					<li>Text Corpus for</li>
					<ul class="c"> 
						<li>Kurdish Kobani, Morisien Creole, Vietnamese, Chinese</li>
					</ul>
					<li>Novel Data</li>
					<ul class="c"> 
						<li>via scraping the internet + cleaning</li>
						<li>via translations from English</li>
						<li>via image descriptions by native speakers</li>
					</ul>
					<li>Previous Data</li>
					<ul class="c"> 
						<li>from available mono- and multi-lingual datasets</li>
					</ul>
				</ul>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > Auxiliary Project: CRAMT </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto; mx-auto my-auto;">
				<a href="https://github.com/christianschuler8989/CRAMT">
					<img src="CRAMT-Tool-Logo.png" alt="CRAMT Logo" class="w-[90vw]">
					<figcaption class="text-[2.3vh]">
						Cross-Lingual Resource Aggregation of Low-Resource Machine Translation and Metadata 
					</figcaption>
				</a>
				<ul class="b" >
					<li>1. Text Corpus for specific target languages aiming to provide new aligned text data.</li>
					<br>
					<li>2. Analysis of the collected and aligned data.</li>
					<ul class="c"> 
						<li>Some help to get a quick idea of the data distribution such as generated word clouds,</li>
						<li>but also reports to provide deeper insights about the data.</li>
					</ul>
					<br>
					<li>3. Datasheet that can represent and explain the newly created dataset and its purpose.</li>
				</ul>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<Slide><Layout>
		<titlebar > The End </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto; mx-auto my-auto;">
				<a href="https://github.com/Low-ResourceDialectology/TextAsCorpusRep">
					<img src="TextAsCorpusRep-Auxiliary-Logo.png" alt="MTACR Logo" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						Main Project: TextAsCorpusRep
					</figcaption>
					<figcaption class="text-[1.3vh]">
						Multilingual Text As Corpus Repository for Machine Translation of Low-Resource Language
					</figcaption>
				</a>
				<a href="https://github.com/christianschuler8989/CRAMT">
					<img src="CRAMT-Tool-Logo.png" alt="CRAMT Logo" class="h-[30vh]">
					<figcaption class="text-[2.3vh]">
						Auxiliary Project: CRAMT
					</figcaption>
					<figcaption class="text-[1.3vh]">
						Cross-Lingual Resource Aggregation of Low-Resource Machine Translation and Metadata 
					</figcaption>
				</a>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<script> newChapter("Appendix"); </script>
	<Slide><Layout>
		<titlebar > References </titlebar>
		<mybody>
			<div class="grid" style="grid-template-columns: auto auto auto; mx-auto my-auto;">
				<div>
					<div class="text-[3.0vh]">
						MTACR-Related (TODO)
					</div>
					<ul class="a" >
						<li>Author, (Date)</li>
						<li>Author et al., (Date)</li>
					</ul>
				</div>
				<div>
					<div class="text-[3.0vh]">
						CRAMT-Poster-Related
					</div>
					<ul class="a" >
						<li>Ahmadi, (2020)</li>
						<li>Yu, et al., (2022)</li>
						<li>Artetxe, et al., (2022)</li>
						<li>Kreutzer, et al., (2022)</li>
						<li>Vulić, et al., (2013)</li>
						<li>Gouws, et al., (2016)</li>
						<li>Bafna, et al., (2023)</li>
						<li>Karakante, et al., (2018)</li>
						<li>Reimers, et al., (2020)</li>
						<li>de Vries, et al., (2021)</li>
						<li>Yimam, et al., (2020)</li>
						<li>Millour, et al., (2020)</li>
						<li>Lent, et al., (2022)</li>
						<li>Liu, et al., (2022)</li>
						<li>Cahyawijaya, et al., (2023)</li>
						<li>Pei, et al., (2022)</li>
						<li>Kargaran, et al., (2023)</li>
						<li>Haig, (2001)</li>
					</ul>
				</div>
				<div>
					<div class="text-[3.0vh]">
						CRAMT-Paper-Related (TODO)
					</div>
					<ul class="a" >
						<li>Author, (Date)</li>
						<li>Author et al., (Date)</li>
					</ul>
				</div>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual presentation.<br>
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide>

	<!-- to mimic the latex template  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length;
		const totalChapters = chapterNames.length;
		var temp; 
		for (let i = 0; i < totalSlides; i++) {
			// one section, one slide
			document.getElementsByTagName('section')[i].setAttribute("id", "slide-"+(i+1));
			// add author name 
			document.getElementsByTagName('author')[i].innerText=authorshort;
			// add title 
			document.getElementsByTagName('mytitle')[i].innerHTML="<a href=\"#slide-1\">"+title+"</a>";
			// show slide number with total slide number
			document.getElementsByTagName("pagenumber")[i].innerHTML = (i+1)+"/"+totalSlides;
		}
		for (let i = 0; i < totalSlides; i++) {
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				temp = document.querySelectorAll("table.topbar")[i]; 
				temp.getElementsByTagName("tr")[0].innerHTML += "<th data-chpcol=\"chpcol\" style=\"font-weight:normal\">"+chapterNames[j]+"</th>";
				// document.getElementsByTagName("test")[0].innerHTML="here!"; 
				// fill in dots
				let slidesInChapter = presentationData.filter(item => item.chapter == chapterNames[j]);
				let begin = slidesInChapter[0].pagenr;
				let end = slidesInChapter[slidesInChapter.length-1].pagenr;
				let circles=toCircle(begin,end);
				temp.getElementsByTagName("tr")[1].innerHTML += "<td>"+ circles +"</td>";
			}
		}
		for (let i = 0; i < totalSlides; i++) {
			// first, find out if title page and toc exist 
			let chapter0 = presentationData.filter(item => item.chapternr == 0).length;
			if (i>=chapter0){
				// then set corresponding circle to white
				let circle = document.getElementsByTagName("circle-"+(i+1))[i]; 
				circle.style.background="white";
				circle.style.border="0px";
				// also the chapter names 
				let chapterNr = presentationData.filter(item => item.pagenr == i+1)[0].chapternr;
				temp = document.getElementsByTagName("th")[(i)*(totalChapters)+chapterNr-1];
				if (temp.hasAttribute("data-chpcol")){ 
					temp.style.color="white";
				}
			}
		}
		// circles: start, start+1, . . . , end are created
		function toCircle(begin,end){
			let circles = ""; 
			for (let i=begin; i<=end; i++){
				circles+="<a href=\"#slide-" +i+ "\"><circle-" +i+ " class=\"dot\"> </circle-" +i+ "> </a>" ;
			}
			return circles;
		}
		// to create table of contents
		if (toc) {
			for (i=1; i<=chapterNames.length;i++){
				document.getElementsByTagName('chpicons')[0].innerHTML += "<div class=\"chpicon\">"+i+"</div> <br>";
				document.getElementsByTagName('chpnames')[0].innerHTML += "<div>"+chapterNames[i-1]+"</div> <br>";
			}
		}
	</script>
	
	<style>
		.chpicon{
			color: white;
			width:180%;
			background: var(--themecolor);
		}
		.dot {
			height: 15px;
			width: 15px;
			background: rgba(0,0,0,0);
			border-radius: 50%;
			border: 1.5px solid var(--themecolorlight);
			display: inline-block;
		}
		ul.a {
			list-style-type: square;
			padding-top:5vh;
			font-size:2.5vh;
		}
		ul.b {
			list-style-type: circle;
			margin-left:5vh;
			margin-right:5vh;
			padding-top:1vh;
			padding-bottom:1vh;
			font-size:3.5vh;
		}
		ul.c {
			list-style-type: disc;
			margin-left:10vh;
			margin-right:5vh;
			padding-top:1vh;
			padding-bottom:1vh;
		}
		ul.d {
			list-style-type: circle;
			margin-left:10vh;
			margin-right:5vh;
			padding-top:1vh;
			padding-bottom:1vh;
			font-size:3.5vh;
		}
		ul.d li {
			padding-top:0vh;
			line-height:4.5vh;
		}
		ul{
			text-align: left;
			margin-left:20vh;
			margin-right:5vh;
			padding-top:1vh;
			padding-bottom:1vh;
		}
		titlebar{
			display:flex;
			background: rgb(242,242,242); 
			width: 100vw; 
			height: 9vh; 
			text-align: left;
			padding-left: 5vh; 
			padding-top: 2vh;
			font-size: 5vh;
		}
		mybody{
			display: flex;
			justify-content: center;
			align-items: center;
			height:79vh;
		}
		figure {
			border: 0px #cccccc solid;
			padding: 4px;
			margin: auto;
		}
		figcaption {
			background-color: rgb(242,242,242);
			color: black;
			font-style: italic;
			padding: 2px;
			text-align: center;
		}
	</style>
</Presentation>
