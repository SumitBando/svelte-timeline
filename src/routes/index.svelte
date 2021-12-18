<script>
  import Timeline  from "$lib/Timeline.svelte";
	const events = [
		{
			title: 'Step1',
      date: 'Dec 18, 2021',
      status: 'success'      
    },
    {
			title: 'Step2',
      status: 'error'
    },
    {
			title: 'Step3',
    }
  ]
</script>
<Timeline/>