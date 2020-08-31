<script>
    export let hashtag;

</script>
<div class='big-header-container'>
    <h1>Cari Hashtag Di Instagram</h1>
    <h3>#{hashtag}</h3> 
</div>

<style>
    .big-header-container {
        text-align: center;
    }
    
    h1 {
        color: black;
        font-size: 4em;
        font-weight: 200;
        text-transform: capitalize;
        margin: 10px 0 15px;
    }
    
    h3 {
        color: #ff3000;
        text-transform: uppercase;
        font-size: 2.5em;
        font-weight: 100;
        text-align: center;
        margin: 0;
        padding: 0;
    }

    @media screen and (max-width: 600px) {
        h3 {
            font-size: 2em;
        }
    }
</style>