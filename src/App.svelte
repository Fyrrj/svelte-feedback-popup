<script>
	import FeedbackForm from './components/FeedbackForm.svelte';
	import FeedbackList from './components/FeedbackList.svelte';
	import FeedbackStats from "./components/FeedbackStats.svelte";
	let feedback = [
		{
			id:  1,
			rating: 10,
			text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla nunc felis, molestie eu lacus quis, placerat volutpat mauris. Donec feugiat urna eget enim viverra sodales. Mauris eu massa at libero dignissim gravida non at est. Proin quis facilisis leo."
		},
		{
			id: 2,
			rating: 9,
			text: "Sed sagittis vestibulum lobortis. In nisl nibh, tincidunt quis lorem eget, auctor auctor leo. Ut at scelerisque erat, a pulvinar purus. Sed vel lacinia est. Sed ut laoreet neque. Quisque faucibus iaculis nunc, vitae scelerisque urna consequat vel."
		},
		{
			id: 3,
			rating: 8,
			text: "Nulla et purus sed odio dignissim ornare vitae quis orci. Suspendisse elit lacus, aliquam vitae commodo eu, dapibus et mi. Sed ex neque, iaculis nec velit vitae, vestibulum vulputate massa. Nullam id luctus odio. Integer gravida at ligula ut dapibus."
		}
	]

	$: count = feedback.length;
	$: average = feedback.reduce((a, {rating}) => a + rating, 0) / feedback.length;

	const addFeedback = (e) => {
		const newFeedback = e.detail;
		feedback = [newFeedback, ...feedback]
	}

	const deleteFeedback = (e) => {
		const itemId = e.detail;
		feedback = feedback.filter((item) =>  item.id != itemId)
	}

</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback}/>
	<FeedbackStats {count} {average} />
	<FeedbackList {feedback} on:delete-fedback={deleteFeedback}/>
</main>

<style>

</style>