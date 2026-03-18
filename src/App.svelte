<script lang="ts">
	import './app.css';
	import Button from '$lib/components/ui/button/button.svelte';
	import Label from '$lib/components/ui/label/label.svelte';
	import Input from '$lib/components/ui/input/input.svelte';
	
	// Login form state
	let email = ''
	let password = ''
	let showPassword = false
	
	// Routing state
	let currentView: 'login' | 'signup' | 'welcome' = 'login'
	
	// Signup form state
	let firstName = ''
	let lastName = ''
	let contactNumber = ''
	let birthdate = ''
	let gender = ''
	let signupEmail = ''
	let signupPassword = ''
	let confirmPassword = ''
	let showSignupPassword = false
	let showConfirmPassword = false
	
	function goToSignup() {
		currentView = 'signup'
	}
	
	function goToLogin() {
		currentView = 'login'
	}
	
	function handleLogin(e: Event) {
		e.preventDefault()
		currentView = 'welcome'
	}
</script>

<div class="min-h-screen flex flex-col items-center justify-center bg-pink-50">
	{#if currentView === 'login'}
	<!-- Login Form -->
	<form on:submit={handleLogin} class="p-8 rounded-xl shadow-lg w-100 h-1000px flex flex-col gap-6
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
				class="text-lg"
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
				class="text-lg pr-12"
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
      			<button 
				type="button"
				on:click={goToSignup}
				class="text-pink-500 hover:text-pink-700 font-semibold">
				Sign up</button>
			</div>
	</form>
	{:else}
	<!-- Signup Form -->
	<form class="p-8 rounded-xl shadow-lg w-100 flex flex-col gap-4
               bg-pink-100 border-7 border-pink-300">
		<h1 class="text-xl font-extrabold text-center text-pink-500">
  			Create Your Account</h1>
		
		<!-- Name Fields -->
		<div class="flex gap-4">
			<div class="flex flex-col gap-1 flex-1">
				<Label>First Name</Label>
				<Input
					id="firstName"
					type="text"
					placeholder="First name"
					bind:value={firstName}
					class="text-lg"
				/>
			</div>
			<div class="flex flex-col gap-1 flex-1">
				<Label>Last Name</Label>
				<Input
					id="lastName"
					type="text"
					placeholder="Last name"
					bind:value={lastName}
					class="text-lg"
				/>
			</div>
		</div>
		
		<!-- Contact Number -->
		<div class="flex flex-col gap-1">
			<Label>Contact Number</Label>
			<Input
				id="contactNumber"
				type="tel"
				placeholder="Enter your contact number"
				bind:value={contactNumber}
				class="text-lg"
			/>
		</div>
		
		<!-- Birthdate -->
		<div class="flex flex-col gap-1">
			<Label>Birthdate</Label>
			<Input
				id="birthdate"
				type="date"
				bind:value={birthdate}
				class="text-lg"
			/>
		</div>
		
		<!-- Gender -->
		<div class="flex flex-col gap-1">
			<Label>Gender</Label>
			<select
				id="gender"
				bind:value={gender}
				class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2"
			>
				<option value="" disabled selected>Select gender</option>
				<option value="male">Male</option>
				<option value="female">Female</option>
				<option value="other">Other</option>
				<option value="prefer-not-to-say">Prefer not to say</option>
			</select>
		</div>
		
		<!-- Email -->
		<div class="flex flex-col gap-1">
			<Label>Email</Label>
			<Input
				id="signupEmail"
				type="email"
				placeholder="Enter your email"
				bind:value={signupEmail}
				class="text-lg"
			/>
		</div>
		
		<!-- Password -->
		<div class="flex flex-col gap-1 relative">
			<Label>Password</Label>
			<Input
				id="signupPassword"
				type={showSignupPassword ? 'text' : 'password'}
				placeholder="Create a password"
				bind:value={signupPassword}
				class="text-lg pr-12"
			/>
			<button
				type="button"
				class="absolute right-2 top-2 transform -translate-y-1/2 text-sm font-semibold text-gray-500 hover:text-gray-700"
				on:click={() => (showSignupPassword = !showSignupPassword)}
			>
				{showSignupPassword ? 'Hide' : 'Show'}
			</button>
		</div>
		
		<!-- Confirm Password -->
		<div class="flex flex-col gap-1 relative">
			<Label>Confirm Password</Label>
			<Input
				id="confirmPassword"
				type={showConfirmPassword ? 'text' : 'password'}
				placeholder="Confirm your password"
				bind:value={confirmPassword}
				class="text-lg pr-12"
			/>
			<button
				type="button"
				class="absolute right-2 top-2 transform -translate-y-1/2 text-sm font-semibold text-gray-500 hover:text-gray-700"
				on:click={() => (showConfirmPassword = !showConfirmPassword)}
			>
				{showConfirmPassword ? 'Hide' : 'Show'}
			</button>
		</div>
		
		<Button type="submit" class="w-full bg-pink-300 border-2">Sign Up</Button>

		<!-- Back to Login -->
		<div class="mt-2 text-center text-sm text-gray-500"> Already have an account? 
      			<button 
				type="button"
				on:click={goToLogin}
				class="text-pink-500 hover:text-pink-700 font-semibold">
				Login</button>
			</div>
	</form>
	{:else if currentView === 'welcome'}
	<!-- Welcome Screen -->
	<div class="p-8 rounded-xl shadow-lg w-100 h-1000px flex flex-col gap-6 items-center justify-between
               bg-pink-100 border-7 border-pink-300">
		<div class="w-full flex justify-start">
			<button
				type="button"
				on:click={goToLogin}
				class="text-pink-500 hover:text-pink-700 font-semibold text-sm"
			>
				← Back
			</button>
		</div>
		
		<h1 class="text-4xl font-extrabold text-center text-pink-500">
			Welcome to PinkyPal
		</h1>
		
		<p class="text-lg text-center text-gray-700 font-semibold">
			this your friendly menstruation tracker-- let's start!
		</p>
	</div>
	{/if}
</div>
