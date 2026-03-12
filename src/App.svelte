<script lang="ts">
	import './app.css';
	import Button from '$lib/components/ui/button/button.svelte';
	import Label from '$lib/components/ui/label/label.svelte';
	import Input from '$lib/components/ui/input/input.svelte';
	
	let email = ''
	let password = ''
	let showPassword = false
</script>

<div class="min-h-screen flex flex-col items-center justify-center bg-pink-50">
	<form class="p-8 rounded-xl shadow-lg w-100 h-1000px flex flex-col gap-6
               bg-pink-100 border-7 border-pink-300">
		<h1 class="text-xl font-extrabold text-center text-pink-500 font[Times New Roman]">
  					Welcome to PinkyPal</h1> 			 	
		<!-- Email Field -->
		<div class="flex flex-col gap-1">
			<Label>Email</Label>
			<Input
				id="email"
				type="email"
				placeholder="Enter your email"
				bind:value={email}
				class="text-lg font-bold"
			/>
		</div>
		<!-- Password Field -->
		<div class="flex flex-col gap-1 relative">
			<Label>Password</Label>
			<Input
				id="password"
				type={showPassword ? 'text' : 'password'}
				placeholder="Enter your password"
				bind:value={password}
				class="text-lg pr-12 font-bold"
			/>

		<!-- Submit Button -->
			<button
				type="button"
				class="absolute right-2 top-2 transform -translate-y-1/2 text-sm font-semibold text-gray-500 hover:text-gray-700"
				on:click={() => (showPassword = !showPassword)}
			>
				{showPassword ? 'Hide' : 'Show'}
			</button>
		</div>
		<Button type="submit" class="w-full bg-pink-300 border-2">Login</Button>

		<!-- Sign Up Field-->
		<div class="mt-4 text-center text-sm text-gray-500"> Don't have an account? 
      			<a 
				href="/register" 
				class="text-pink-500 hover:text-pink-700 font-semibold">
				Sign up</a>
			</div>
	</form>
</div>
