<script>
    import supabase from "$lib/db.js";
	import SignUp from "../../../components/SignUp.svelte";

    let email = "";
    let password = "";
  
    const usersignup = async () => {
      const { user, session, error } = await supabase.auth.signUp({
        email: email,
        password: password,
      });
      console.log(user, session, error);
      email = "";
      password = "";
    };
  </script>

  <SignUp />

