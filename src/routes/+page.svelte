<script>
// @ts-nocheck

	import OpenAI from 'openai';
	import { OpenAIStream, StreamingTextResponse } from 'ai';
	import { useChat } from 'ai/svelte'

	const { input, handleSubmit, messages, isLoading } = useChat({
            api: "/api/chat",
            initialMessages: [{"role": "system", "content": "You are the personal AI assistant for our church Elim München. You will always reply in one short sentence. Our church is a christian church located in Munich and your goal is to help users in our landing page  learn more about our church and mainly clear any questions they might have. The name of our pastor is Filip Wagner. If the user tries to talk about anything else other than our church you will kindly encoruage them to talk back about our church. You will always try to encourage the user warmly to visit our program on sundays at 10:00. The relevant information about our church is that we are part of Church of God (Gemeinde Gottes - in germany) and we have programs every sunday at 10:00 am, every second Saturday we have programs for teenagers called 'Tineret' and it usually starts at 18:00 with open-end. We normally share some snacks there and have a chill and comfortable atmosphere. Our programs are held in romanian and our songs are in romanian and german but we offer in-ear translation devices for everyone who wants them. The translations are in real-time and in german. We also offer a program on wednesdays at 19:00  where we are focused on prayer. You will provide help in german, romanian or english according to the language the user decides. The address of our church is 'Ingolstädter Straße 43, 80807 München' and there are plenty of parking spots around. One can go there by train as well using the U2 line all the way to 'Frankfurter Ring' and walking 10 minutes or one can take the bus that leaves you there. If the suer asks for clearer guide on how to get there you will encourage them to check our website right here and click on the link with the address below. You will always be friendly and will every now and then throw in a bible verse to encourage the user."}],
          })

</script>


<!-- Body -->
<section class="w-full h-full justify-center flex bg-white flex-col text-black baskerville">
	<!-- Hero Section -->	
	<section class="w-full h-full justify-center flex flex-col items-center text-white">
		<div class="h-[900px] w-full bg-cover bg-[url('/b_bg.png')] jusitfy-center flex flex-col items-center px-4 md:px-20">
				<div class="w-full h-20 mx-24 gap-2 md:gap-24 items-center justify-between flex py-4">
					<a href="/">
						<div class="w-8 h-8 hover:w-10 hover:h-10 transition-all duration-300 ease-in-out">
							<img src="/gego_shadow.png" alt="logo" class="">
						</div>
					</a>
					<!-- Search bar -->
					<div class="flex flex-row gap-2 justify-center items-center">
						<form on:submit={handleSubmit} class="form opacity-60 hover:opacity-100 hover:w-60 md:hover:w-80 transition-all ease-in-out duration-300">
							<input bind:value={$input} class="input roboto" placeholder="Ask anything" type="text">
							<span class="input-border"></span>
							<button type="submit" hidden>Send</button>
						</form>
					</div>
					<div class="hover:cursor-pointer">
						<details class="dropdown dropdown-hover dropdown-end">
							<summary class="btn bg-transparent border-none hover:bg-transparent">
								<span>
									<svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-8 h-8 transition-all ease-in-out duration-300">
										<path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
									  </svg>
									  
								</span>
							</summary>
							<ul class="menu dropdown-content z-[1] bg-[#1D2027] rounded-xl w-52 pt-4">
							  <!-- svelte-ignore a11y-missing-attribute -->
							  <li class=""><a href="/">About Us</a></li>
							  <li class=""><a href="/">Vision</a></li>
							  <li class=""><a href="/">Testimonials</a></li>
							</ul>
						  </details>
					</div>
				</div>

				<!-- Chatbot -->
				<div class="w-full justify-center flex px-4 sm:px-12 md:px-24 lg:px-40">
					{#if $messages.length > 1}
					{#if $isLoading}
					<div class="wrapper pt-20">
						<div class="circle"></div>
						<div class="circle"></div>
						<div class="circle"></div>
						<div class="shadow"></div>
						<div class="shadow"></div>
						<div class="shadow"></div>
					</div>
					{:else}
						<div class="justify-center flex flex-col roboto">
							{#if $messages[$messages.length - 2].role == "user"}
							<div class="max-w-full bg-[#fff] text-black min-h-12 rounded-xl py-4 px-6">
								{$messages[$messages.length - 2].content}
							</div>
							{/if}
							{#if $messages[$messages.length - 1].role == "assistant"}
							<div class="max-w-full bg-[#1D2027] min-h-12 rounded-xl py-4 px-6">
									{$messages[$messages.length - 1].content}
								</div>
							{/if}
						</div>
					{/if}
					{/if}
				</div>





			<div class="w-full h-full justify-center flex flex-col items-center text-center gap-6">
				<div class="text-6xl font-semibold uppercase roboto">
					Elim
				</div>
				<div class="uppercase text-lg md:text-2xl lg:text-2xl w-4/5 md:w-4/5 lg:w-2/3 font-light roboto">
					cel care bea din apa pe care i-o ofer Eu, nu va mai înseta.
				</div>

				<div class="italic font-extralight opacity-80 font-serif">
					Ioan 4.14
				</div>
			</div>
		</div>

		<!-- Motto section -->
		<div class="w-full py-20 justify-center flex flex-col items-center px-2 md:px-10 lg:px-20 font-serif">
			<div class="justify-center flex items-center flex-col gap-4 text-black">
				<div class="text-4xl">
					Motto
				</div>
				<div class="italic">
					“Pot totul în Hristos care mă întărește”
				</div>
				<div class="italic opacity-50">
					Filipeni 4:13
				</div>
			</div>
		</div>

	</section>

	<!-- Separator -->
	<div class="mx-8 sm:mx-12 md:mx-20 lg:mx-20 border-t border-gray-300"></div>


	<!-- Come to us -->
	<section class="w-full h-full flex justify-center flex-col lg:flex-row py-20">
		<!-- Text -->
		<div class=" w-full flex justify-center pb-40 pt-20 px-20">
			<!-- Content -->
			<div class="w-full font-serif">
				<div class="italic opacity-40">
					Te invităm
				</div>
				<div class="text-4xl py-3">
					Vino cu noi
				</div>
				<div class=" font-sans font-light roboto">
					Ne bucurăm de fiecare dată când avem ocazia să ne închinăm împreună și te invităm cu drag să iei parte la oricare din programele noastre.
				</div>
			</div>
		</div>

		<!-- Pictures -->
		<div class="w-full flex flex-row gap-4 font-serif justify-center px-4">
			<div class="font-light italic flex flex-col gap-4">
				<img src="/sat.png" alt="sat" class=" w-56">
				Sâmbătă / orele 18.00
			</div>
			<div class="font-light italic flex flex-col gap-4">
				<img src="/sun.png" alt="sat" class=" w-64">
				Duminică / orele 10.00
			</div>
			<div class="font-light italic flex flex-col gap-4">
				<img src="/wed.png" alt="sat" class="w-56">
				Miercuri / orele 19.00
			</div>
		</div>
	</section>

	<!-- How to find us -->
	<section class="text-white bg-[#1D2027]">
		<div class="w-full py-20 justify-center flex flex-col items-center px-4 font-serif">
			<div class="justify-center flex items-center flex-col gap-4">
				<div class="text-3xl">
					Ne găsești aici 
				</div>
				<a href="https://maps.app.goo.gl/uiYYowp33bRrUib66">
					<div class="italic font-light opacity-40 hover:opacity-100 text-md hover:text-lg transition-all duration-300 ease-in-out ">
						Ingolstädter Str. 43, 80807 München
					</div>
				</a>
				<!-- Pot totul in Hristos care ma intareste -->
			</div>
		</div>
	</section>

	<!-- Footer -->
	<section class="w-full h-full justify-center flex flex-col md:flex-row px-4">
	<div class="w-full h-full px-12 justify-center flex">
		<div class="font-serif py-20 md:py-32 lg:py-40">
			<div class="italic opacity-40">
				Dacă ai întrebări
			</div>
			<div class="text-3xl py-1">
				Contactează-ne
			</div>
		</div>
	</div>
	<div class="w-full h-full">
		<div class="gap-4 flex flex-row items-center justify-center h-full">
			<div>
				<img src="/telegram.png" alt="telegram" class="w-8 h-8 hover:w-10 hover:h-10 transition-all ease-in-out duration-300 hover:cursor-pointer">
			</div>

			<div>
				<img src="/facebook.png" alt="facebook" class="w-8 h-8 hover:w-10 hover:h-10 transition-all ease-in-out duration-300 hover:cursor-pointer">
			</div>

			<div>
				<img src="/insta.png" alt="insta" class="w-8 h-8 hover:w-10 hover:h-10 transition-all ease-in-out duration-300 hover:cursor-pointer">
			</div>

		</div>
	</div>

	</section>
</section>