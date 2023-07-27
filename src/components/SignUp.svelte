<script>
    import supabase from '$lib/db.js';
    import {slide} from 'svelte/transition';
    

	let email = '';
	let password = '';

    let isvisible=false;

	const usersignup = async () => {
        isvisible=true;
        setTimeout(() => {
            isvisible=false;
        }, 3000);
		const { user, session, error } = await supabase.auth.signUp({
			email: email,
			password: password
		});
		console.log(user, session, error);
		email = '';
		password = '';
		
	

	};
</script>

<div class="flex min-h-full flex-col justify-center px-6 py-12 lg:px-8">
	<div class="sm:mx-auto sm:w-full sm:max-w-sm">
		<img
			class="mx-auto h-20 w-auto"
			src="https://cdn-icons-png.flaticon.com/512/5345/5345491.png"
			alt="Your Company"
		/>
		<h2 class="mt-10 text-center text-2xl font-bold leading-9 tracking-tight text-white">
			Create account
		</h2>
	</div>

	<div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
		<form class="space-y-6" on:submit|preventDefault={usersignup}>
			<div>
				<label for="email" class="block text-sm font-medium leading-6 text-white"
					>Email address</label
				>
				<div class="mt-2">
					<input
						id="email"
						name="email"
						type="email"
						autocomplete="email"
						required
						class="block w-full rounded-md border-0 bg-white/5 py-1.5 text-white shadow-sm ring-1 ring-inset ring-white/10 focus:ring-2 focus:ring-inset focus:ring-indigo-500 sm:text-sm sm:leading-6"
						bind:value={email}
					/>
				</div>
			</div>

			<div>
				<div class="flex items-center justify-between">
					<label for="password" class="block text-sm font-medium leading-6 text-white"
						>Password</label
					>
					<div class="text-sm">
						<a href="#" class="font-semibold text-indigo-400 hover:text-indigo-300"
							>Forgot password?</a
						>
					</div>
				</div>
				<div class="mt-2">
					<input
						id="password"
						name="password"
						type="password"
						autocomplete="current-password"
						required
						class="block w-full rounded-md border-0 bg-white/5 py-1.5 text-white shadow-sm ring-1 ring-inset ring-white/10 focus:ring-2 focus:ring-inset focus:ring-indigo-500 sm:text-sm sm:leading-6"
						bind:value={password}
					/>
				</div>
			</div>

			<div>
				<button
					type="submit"
					class="flex w-full justify-center rounded-md bg-indigo-500 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-500"
					>Sign up</button
				>
			</div>
		</form>

		<p class="mt-10 text-center text-sm text-gray-400">
			Already have an account?
			<a href="/signIn" class="font-semibold leading-6 text-indigo-400 hover:text-indigo-300"
				>Sign In</a
			>
		</p>
	</div>
</div>

<div>
    {#if isvisible }
    <div class="alert alert-success w-96 absolute right-2 bottom-10 " transition:slide >
        <svg xmlns="http://www.w3.org/2000/svg" class="stroke-current shrink-0 h-6 w-6" fill="none" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>
        <span>Check your email for confirmation link</span>
      </div>
    {/if}
</div>


