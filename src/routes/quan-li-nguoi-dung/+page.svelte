<script>
    import {onMount} from "svelte";
    
    let users = [];

    onMount(async () => {
        const res = await fetch(`http://10.0.2.14:3000/user`);
        users = (await res.json()).data;
    })
</script>

<a href="quan-li-nguoi-dung/them-nguoi-dung">Them moi</a>

<table>
    <thead>
        <th>STT</th>
        <th>Ho va Ten</th>
        <th>Username</th>
        <th>Email</th>
        <th>Trang thai</th>
    </thead>

    <tbody>
        {#each users as user, i(i)}
            <tr>
                <td>{i+1}</td>
                <td>{user.full_name}</td>
                <td>{user.username}</td>
                <td>{user.email}</td>
                <td>{user.active}</td>
            </tr>
        {/each}
    </tbody>
</table>