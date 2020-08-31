<script>
	import BigHeader from './components/BigHeader/BigHeader.svelte';
	import PhotoList from './components/PhotoList/PhotoList.svelte';

	export let hashtag;

</script>

<main>
	<BigHeader hashtag={hashtag}/>
	<PhotoList hashtag={hashtag}/>
</main>

<style>
 
</style>