<script>
	import { fade, slide } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import Star from './Star.svelte';
	
	// User rating states
	export let rating = null;
	let hoverRating = null;
	
	// form interaction states
	let collectFeedback = false;
	let feedbackCompleted = false;
	
	// "$:" triggers when something in the line changes
	// When these variables reach true/false, they trigger these functions
	$: collectFeedback && addWatchListeners();
	$: !collectFeedback && feedbackFormClosed();
	
	function feedbackFormClosed() {
		feedbackCompleted = false;
		removeWatchListeners()
	}
	
	function addWatchListeners() {
		document.addEventListener('keydown', userDismissFeedback);
		document.addEventListener('click', userClickedOutsideOfFeedback);
	}
	function removeWatchListeners() {
		document.removeEventListener('keydown', userDismissFeedback);
		document.removeEventListener('click', userClickedOutsideOfFeedback);
	}
	function userClickedOutsideOfFeedback(event) {
		const container = document.getElementById('feedbackContiner');
		if (!container.contains(event.target)) {
			collectFeedback = false;
		}
	}
	function userDismissFeedback(event) {
			switch(event.key) {
				case 'Escape':
					collectFeedback = false;
					break;
				default:
					return;
			}
		}
	
	// using curried function to initialize hover with id
	const handleHover = (id) => () => {
		hoverRating = id;
	}
	const handleRate = (id) => (event) => {
		if (collectFeedback && 
				rating && 
				rating.toString() === event.srcElement.dataset.starid
		) {
			collectFeedback = false;
			return;
		}
		rating = id;
		collectFeedback = true;
	}
	
	let stars = [
		{ id: 1, title: 'One Star' },
		{ id: 2, title: 'Two Stars' },
		{ id: 3, title: 'Three Stars' },
		{ id: 4, title: 'Four Stars' },
		{ id: 5, title: 'Five Stars' },
	]

	function handleCollectFeedback(e) {
		const textarea = e.srcElement.querySelector('textarea');
		const value = textarea.value;
		
		// let them know we recieved it
		feedbackCompleted = true;
		
		// then reset view
		setTimeout(() => {
			collectFeedback = false;
			feedbackCompleted = false;
		}, 1250);
	}
	
	function handleLinkFeedback() {
		collectFeedback = true; 
	}
</script>
<style>
	.feedback {
		position: relative;
	}
	.collectFeedbackContainer {
		width: 300px;
		position: absolute;
		top: 44px;
		left: 0;
		background: #fff;
		border: 1px solid #666;
		padding: 8px;
		transition: transform .2s ease-out;
	}
	.collectFeedbackContainer textarea {
		display: block;
		width: 100%;
		height: 120px;
		resize: none;
	}
	.cancel {
		background: none;
		text-decoration: underline;
		border: none;
	}
	.starContainer {
		display: inline-block;
		transition: background .2s ease-out;
		border-radius: 8px;
		padding: 4px 6px 0;
	}
	.feedbackContainer:hover .starContainer {
		background: rgba(255,255,255,0.4);
	}
	.secondaryAction {
		margin: 8px;
		font-size: 12px;
		display: inline-block;
	}
	.feedbackContainerDisabled {
		pointer-events: none;
	}
	:global(button) {
		cursor: pointer;
	}
</style>

<div class="feedback"> 
	<span id="feedbackContiner" class="feedbackContainer" class:feedbackContainerDisabled={feedbackCompleted}>
		<span class="starContainer">
		{#each stars as star (star.id)}
			<Star 
					filled={hoverRating ? (hoverRating >= star.id) : (rating >= star.id)} 
					starId={star.id}
					on:mouseover={handleHover(star.id)} 
					on:mouseleave={() => hoverRating = null}
					on:click={handleRate(star.id)}
				/>
		{/each}
				</span>
</div>