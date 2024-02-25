<script>
    const colors = ['red', 'green', 'blue'];
</script>

<div>


    {#each colors as color, i}
        <button
                style="background: {color};"
                on:click={ () => {console.log(`click sur ${color} - ${i}`)} }
        ></button>
    {/each}
</div>