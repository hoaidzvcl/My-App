<script>
    import {goto} from "$app/navigation"
    let user = {};

    async function luu(){
        let res = await fetch("http://10.0.2.14:3000/user",{
            method: "POST",
            body: JSON.stringify(user),
            headers: {
                'Content-Type': 'application/json',
            }
        })
        if (res.ok) {
            goto("/quan-li-nguoi-dung");
        } else {
            alert("Them moi that bai")
        }
    };
</script>

{JSON.stringify(user)};

<form action="" on:submit={luu}>
    <label for="full-name">Ho va ten</label>
    <input id="full-name" type="text" bind:value={user.full_name}>
    <label for="username">Username</label>
    <input id="username" type="text" bind:value={user.username}>
    <label for="email">Email</label>
    <input id="email" type="email" bind:value={user.email}>
    <label for="mat-khau">Password</label>
    <input id="mat-khau" type="password" bind:value={user.password}>

    <button type="submit">Luu</button>
</form>