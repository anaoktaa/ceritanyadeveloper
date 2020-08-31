<script>
    import { onMount } from 'svelte';
    export let hashtag;

    let photos = [];
    onMount(async function() {
        try {
        const res = await fetch(`https://www.instagram.com/explore/tags/ceritanyadeveloper/?__a=1`);
        const data = await res.json();
            photos = data.graphql.hashtag.edge_hashtag_to_media.edges;
        } catch (err) {
            console.error(err);
        }
    });
  
    function truncate_words(text, length) {
        if (text.length <= length) {
            return text;
        }
        else {
            return `${text.slice(0, length)} . . . `;
        }
    }
</script>

<div>
    <!-- <div class='input-search-container'>
        <input class='search-input' name='hashtag' type='text' bind:value={hashtag}/>
    </div> -->
    <div class='photo-list-container'>
        {#each photos as photo}
            <div class='photo-grid'>
                <div class='photo-container'>
                    <img src="{photo.node.thumbnail_src}" alt="thumbnail" width='100%' height='100%'>
                </div>
    
                <div class='photo-description'>
                    <p>{truncate_words(photo.node.edge_media_to_caption.edges[0].node.text, 200)}</p>
                </div>
            </div>
        {/each}
    </div>
</div>

<style>
     .input-search-container {
		padding: 20px 0 0;
		display: flex;
		flex-direction: column;
		align-items: center;
    }

    .search-input {
        width: 50%;
	}
	
	@media screen and (max-width: 600px) {
		.search-input {
			width: 80%;
			/* padding: 0 20px; */
		}
	}
    .photo-list-container {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 30px;
        margin-top: 50px;
        padding: 0 60px;
        box-sizing: border-box;
    }

    .photo-description {
        padding: 10px 15px;
    }

    .photo-grid {
        margin: 20px 0;
        box-sizing: border-box;
        width: 100%;
        height: 500px;
        box-shadow: 0px 0px 5px #d2d2d2;
        border-radius: 10px;
        overflow-y: hidden;
    }

    .photo-container {
        height: 320px;
        width: 100%;
    }

    @media screen and (max-width: 992px) {
        .photo-list-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            grid-gap: 30px;
            padding: 0 60px;
            box-sizing: border-box;
        }

        .photo-grid {
            height: 520px;
        }
    }

    @media screen and (max-width: 600px) {
        .photo-list-container {
            padding: 0 20px;
            grid-template-columns: 1fr;
        }

        .photo-grid {
            height: 470px;
            margin: 0;
        }
    }


</style>