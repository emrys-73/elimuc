<script>
// @ts-nocheck

	import OpenAI from 'openai';
	import { OpenAIStream, StreamingTextResponse } from 'ai';
	import { animate } from '../stores';
	import { useChat } from 'ai/svelte'
	import Carousel from '$lib/Carousel.svelte';

	const { input, handleSubmit, messages, isLoading, setMessages, reload } = useChat({
            api: "/api/chat",
            initialMessages: [{"role": "system", "content": "You are the personal AI assistant for our church Elim München. You will always reply in one short sentence. Our church is a christian church located in Munich and your goal is to help users in our landing page  learn more about our church and mainly clear any questions they might have. The name of our pastor is Filip Wagner. Thedy Wagner is the pastor's wife. Joy Wagner and Grace Wagner are their daughters. Sorin Wagner is in charge of the finances. Sorin Wagner is the husband of Filip's sister.   If the user tries to talk about anything else other than our church you will kindly encoruage them to talk back about our church. You will always try to encourage the user warmly to visit our program on sundays at 10:00. The relevant information about our church is that we are part of Church of God (Gemeinde Gottes - in germany) and we have programs every sunday at 10:00 am, every second Saturday we have programs for teenagers called 'Tineret' and it usually starts at 18:00 with open-end. We normally share some snacks there and have a chill and comfortable atmosphere. Our programs are held in romanian and our songs are in romanian and german but we offer in-ear translation devices for everyone who wants them. The translations are in real-time and in german. We also offer a program on wednesdays at 19:00  where we are focused on prayer. You will provide help in german, romanian or english according to the language the user decides. The address of our church is 'Ingolstädter Straße 43, 80807 München' and there are plenty of parking spots around. One can go there by train as well using the U2 line all the way to 'Frankfurter Ring' and walking 10 minutes or one can take the bus that leaves you there. If the suer asks for clearer guide on how to get there you will encourage them to check our website right here and click on the link with the address below. You will always be friendly and will every now and then throw in a bible verse to encourage the user."}],
			onFinish: () => {
				activeBot = true
			}
          })


	const about = "Biserica română din München dorește să fie un mijloc pentru răspândirea veștii bune a lui Isus Hristos atât pentru locuitorii de naționalitate română din München cât si pentru cei de naționalitate germană. Să fim locul în care cei răniți sufletește, deprimați si confuzi să poată gasi dragoste, acceptare, iertare, ajutor, sperantă, călăuzire si încurajare. "

	let activeBot = false


	const clearChat = () => {
		activeBot = false
		setMessages([])
	}
	
	const images = [
		{title: "Joy", src:"/photos/jlu.jpeg"},
		{title: "team", src:"/photos/team.jpg"},
		{title: "beach", src:"/photos/beach.jpg"},
		{title: "sorin", src:"/photos/sorin.jpg"},
		{title: "Noah & Rares", src:"/photos/nora.jpg"},
	]


</script>



<!-- Body -->
<div class="w-full h-full flex flex-col font-sans bg-white relative">
	<div class="w-full bg-black h-20 z-50 justify-between items-center flex py-8 ">


		<!-- Chatbot -->
		
			<div class="{$animate} absolute  {activeBot ? 'opacity-100 top-20' : 'opacity50 -top-40'} w-full max-h-[400px] overflow-auto z-50 justify-center px-4 md:px-12 lg:px-20 xl:px-40 items-center">
				<div class=" w-full flex rounded-2xl altashadow-2xl text-white flex-col overflow-hidden">
					<div class=" {$animate} {$isLoading ? 'hidden' : 'flex'} bg-transparent w-full text-start font-light px-4 py-2 justify-between flex-row flex">
						<button  on:click={reload}>
							<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
								<path stroke-linecap="round" stroke-linejoin="round" d="M16.023 9.348h4.992v-.001M2.985 19.644v-4.992m0 0h4.992m-4.993 0 3.181 3.183a8.25 8.25 0 0 0 13.803-3.7M4.031 9.865a8.25 8.25 0 0 1 13.803-3.7l3.181 3.182m0-4.991v4.99" />
							  </svg>
							  
						</button>
						<button  on:click={clearChat}>
							<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
								<path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
							  </svg>
							  
						</button>


					</div>
					{#each $messages as m}
						{#if m.role == "assistant"}
							<div class="bg-[#1e1e1e] w-full text-start font-light px-4 py-2 justify-center">
								{m.content}
							</div>

						{/if}
						{#if m.role == "user"}
							<div class="bg-[#060606] w-full text-start font-light px-4 py-2 justify-center">
								{m.content}
							</div>

						{/if}
					{/each}

					
				</div>
			</div>

		

		<a href="/" class="items-center justify-center pl-4">
			<img src="/full_logo.png" alt="BEM" class="h-14">
		</a>

		<!-- <div class="{$animate} text-white opacity-80 hover:opacity-100">
			<a href="/#map" class="">
				Find Us
			</a>
		</div> -->

		<div class=" h-full flex items-center justify-center text-white pr-4">
			<form on:submit={handleSubmit} class="relative">
				<input type="text" placeholder="Începe o conversație" bind:value={$input} class="{$animate} w-[60vw] px-6 pr-12 rounded-full placeholder:opacity-60 max-w-[300px] focus:max-w-[800px] bg-transparent">
				<button type="submit" class="absolute right-4 top-2">
					🔍
				</button>
			</form>
		</div>			
	</div>

	<div class="w-full h-[85vh] relative flex flex-col shrink-0">
		<div class="absolute top-0 z-40 w-full h-60 bg-gradient-to-b from-black to-transparent">

		</div>

		<div class="w-full h-full bg-black absolute top-0 z-10 opacity-50"/>

		

		

		<video class="absolute w-full h-full object-cover z-0" muted autoplay loop playsinline disablepictureinpicture>
			<source src="/videos/hero.mp4" type="video/mp4" />
		</video>

		<!-- Content -->
		<div class="w-full h-full flex flex-col justify-center items-center relative z-40 text-white gap-4">
			<h1 class="text-7xl font-semibold w-full text-center justify-center items-center flex md:px-8">
				Pot totul în Hristos care mă întărește
			</h1>

			<div class="italic font-extralight opacity-80 font-sans">
				Filipeni 4:13
			</div>

			<div class="py-6">
				<a href="/#map">
					<button class="{$animate} px-10 text-center items-center justify-center hover:text-xl py-2 border-white border-2 hover:text-black hover:bg-white hover:px-20 text-white rounded-full font-sans font-bold">
						vino cu noi
					</button>
				</a>
			</div>


		</div>


	</div>


	<div class="w-full h-full flex flex-col px-6 md:px-6 lg:px-12 xl:px-20 pt-4 md:pt-8 lg:pt-10 xl:pt-12 text-black">

		<div class="font-sans flex flex-col pt-12 pb-16 gap-6 px-2 ">
			<h2 class="text-5xl font-bold">
				Te invităm
			</h2>
			<div class=" font-sans font-light roboto w-4/5 md:w-3/4 lg:w-1/2">
				Ne bucurăm de fiecare dată când avem ocazia să ne închinăm împreună și te invităm cu drag să iei parte la oricare din programele noastre.
			</div>
		</div>

		<div class="w-full h-full flex flex-col md:flex-row min-h-[100vh] md:min-h-[60vh] text-white gap-4">

			<div class="{$animate} w-full md:w-[40vw] hover:md:w-[60vw] h-1/3 md:h-full hover:h-1/2 hover:md:h-full shrink-0">
				<a target="_blank" href="https://calendar.google.com/calendar/event?action=TEMPLATE&amp;tmeid=NWY4NzE5OG5iNWY2aDBzMWtnaWI3amQyOWZfMjAyNDAxMTRUMDkwMDAwWiA2MzY3YzIzYzFkNmNjMTAyYzIwNjYwMGU4Mzg5OTc4Y2UxNDRkMWI1YTJlNDFjNzFkN2IyYjM5N2FlNjBhYzE3QGc&amp;tmsrc=6367c23c1d6cc102c206600e8389978ce144d1b5a2e41c71d7b2b397ae60ac17%40group.calendar.google.com&amp;scp=ALL">
				<div class="bg-[url('/photos/hands.png')] bg-image rounded-2xl w-full h-full relative overflow-hidden">
					<div class="absolute bg-gradient-to-b from-transparent to-black w-full h-full opacity-80"/>
						
						<div class="w-full absolute bottom-8 left-8 justify-start">
							<h2 class="text-4xl font-semibold">
								Duminica
							</h2>
							<span class="text-white">
								Orele 10:00
							</span>
						</div>		
					</div>
				</a>
			</div>

			<div class="flex flex-col gap-4  w-full h-full">

				<div class="{$animate} overflow-hidden w-full h-1/2 hover:h-5/6 rounded-2xl bg-[url('/photos/t.jpeg')] bg-image relative">
					<a target="_blank" href="https://calendar.google.com/calendar/event?action=TEMPLATE&amp;tmeid=MDFwazdlZG9yZDA0NzVocmJ2NzdydDRnb2dfMjAyNDAxMTBUMTgwMDAwWiA2MzY3YzIzYzFkNmNjMTAyYzIwNjYwMGU4Mzg5OTc4Y2UxNDRkMWI1YTJlNDFjNzFkN2IyYjM5N2FlNjBhYzE3QGc&amp;tmsrc=6367c23c1d6cc102c206600e8389978ce144d1b5a2e41c71d7b2b397ae60ac17%40group.calendar.google.com&amp;scp=ALL">
						<div class="absolute bg-gradient-to-b from-transparent to-black w-full h-full opacity-80"/>
						
						<div class="w-full absolute bottom-8 left-8 justify-start">
							<h2 class="text-4xl font-semibold">
								Miercuri
							</h2>
							<span class="text-white">
								Orele 19:00
							</span>
						</div>
					</a>
				</div>


				<div class="overflow-hidden w-full h-1/2 hover:h-5/6 rounded-2xl bg-[url('/photos/pnj.jpeg')] bg-image relative">
					<a target="_blank" href="https://calendar.google.com/calendar/event?action=TEMPLATE&amp;tmeid=NDduZ25kcWkwMDI3dTBjMDQ5ZWlxNjBtMHNfMjAyNDAxMTNUMTcwMDAwWiA2MzY3YzIzYzFkNmNjMTAyYzIwNjYwMGU4Mzg5OTc4Y2UxNDRkMWI1YTJlNDFjNzFkN2IyYjM5N2FlNjBhYzE3QGc&amp;tmsrc=6367c23c1d6cc102c206600e8389978ce144d1b5a2e41c71d7b2b397ae60ac17%40group.calendar.google.com&amp;scp=ALL">
					
						<div class="absolute bg-gradient-to-b from-transparent to-black w-full h-full opacity-80"/>
						
						<div class="w-full absolute bottom-8 left-8 justify-start">
							<h2 class="text-4xl font-semibold">
								Sâmbătă
							</h2>
							<span class="text-white">
								Orele 18:00
							</span>
						</div>
					</a>
				</div>

			</div>

		</div>

	</div>


	<div class="w-full h-[100vh] md:h-[100vh] py-10 shrink-0 flex flex-col justify-center items-center">
		<div class=" md:hidden w-full h-full flex flex-col justify-center items-center relative">
			<div class="bg-[url('/photos/team.jpeg')] bg-image h-80 w-full relative flex justify-center items-center py-12 shrink-0">
				<div class="w-full h-full bg-gradient-to-b from-transparent to-black opacity-80 absolute top-0"/>
				<h3 class="text-4xl font-semibold text-white z-50">
					Noi
				</h3>
				

			</div>
			

			
				
		

			<div class="w-full h-full  text-center px-10 text-black flex flex-col gap-4 px-8items-center justify-center">
				

				<p class="font-light">
					{about}
				</p>
			</div>

			
			<!-- <div class="bg-red-500 h-full w-full flex flex-row gap-4 justify-start items-center">
				<div class="bg-[url('/photos/jlu.jpeg')] w-full h-full bg-image">

				</div>
			</div> -->
		</div>

		<!-- Large screen version -->
		<div class="w-full h-full bg-[url('/photos/team.jpeg')] bg-image hidden md:flex relative">
			<div class="w-full h-full bg-gradient-to-b from-transparent to-black opacity-60"/>

			<div class="absolute bottom-16 text-center text-white flex flex-col gap-2 px-20 xl:px-60">
				<h3 class="text-4xl font-semibold">
					Noi
				</h3>

				<p class="font-light">
					{about}
				</p>

				<!-- <Carousel {images}/> -->

			</div>


		</div>

	</div>


	<!-- Maps -->
	<div id="map" class="w-full min-h-[50vh] flex flex-col md:flex-row px-4 text-black md:gap-8 gap-4 md:px-20 shrink-0">
		<div class="rounded-xl justify-center items-center flex w-full min-h-[60vh] md:w-1/2">			
			<iframe class="w-full h-full " title="map" src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d2659.947791628363!2d11.5812019!3d48.1883574!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x479e743b45bfffff%3A0xd137c2e364737a7f!2sBiserica%20Lui%20Dumnezeu%20Elim%20M%C3%BCnchen!5e0!3m2!1sen!2sde!4v1704965435632!5m2!1sen!2sde" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
		</div>

		<div class="md:w-1/2 w-full py-10 md:py-0 h-full flex justify-center items-start flex-col gap-2 ">
			<h3 class="text-4xl font-semibold">
				📍 Ne găsești aici
			</h3>

			<p class="px-3">
				Ingolstädter Str. 43, 80807 München
			</p>

			<p class="px-3 w-3/4 md:w-full font-light py-4">
				S-ar putea să fii aici pentru prima dată, dar deja te privim ca pe o familie.
			</p>

			<div class="py-4 md:py-6">
				<button class="{$animate} px-10 py-2 border-[1px] rounded-full border-black text-lg hover:px-16">
					🔜 🚗 
				</button>
			</div>
	
		</div>


	</div>

</div>