<script>
  export let title = ''
	export let events = [
		{
			title: 'Package Booked',
			date: '21 July 2021, 04:30 PM',
      status: 'success'
		},
		{
			title: 'Out for Delivery',
			date: '22 July 2021, 01:00 PM',
      status: 'success'
		},
		{
			title: 'Cancelled',
			date: 'Customer cancelled the order',
      status: 'error'
		},
		{
			title: 'Delivered'
		}
	];
  const bgColor = (status) => { 
    switch (status) {
      case 'success': return 'bg-green-500'
      case 'error': return 'bg-red-500'
      default: return 'bg-gray-300'
    }
  }
  const textColor = (status) => { 
    switch (status) {
      case 'success': return 'text-white'
      case 'error': return 'text-white'
      default: return 'text-gray-400'
    }
  }
  const icon = (status) => { 
    switch (status) {
      case 'success': return 'fa-check-circle'
      case 'error': return 'fa-times-circle'
      default: return 'fa-exclamation-circle'
    }
  }
</script>
<svelte:head>
  <link
	rel="stylesheet"
	href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.14.0/css/all.min.css"
	integrity="sha512-1PKOgIY59xJ8Co8+NE6FZ+LOAZKjy+KY8iq0G4B3CyeY6wYHN3yt9PW0XpSriVlkMXe40PTKnXrLnZ9+fkDaog=="
	crossorigin="anonymous"
/>
</svelte:head>
<div class="bg-gray-50">
  <div class="p-4 mt-4">
    {#if title}
    <h1 class="text-4xl text-center font-semibold mb-6">{title}</h1>
    {/if}
    <div class="container">
      <div class="flex flex-col md:grid grid-cols-12 text-gray-50">
        {#each events as event}
          <div class="flex md:contents">
            <div class="col-start-2 col-end-4 mr-10 md:mx-auto relative">
                <div class="h-full w-6 flex items-center justify-center">
                  <div class="{bgColor(event.status)} h-full w-1 pointer-events-none"></div>
                </div>
                <div class="{bgColor(event.status)} w-6 h-6 absolute top-1/2 -mt-3 rounded-full shadow text-center">
                  <i class="fas {icon(event.status)} {textColor(event.status)}"></i>
                </div>
            </div>
            <div class="{bgColor(event.status)} col-start-4 col-end-12 p-4 rounded-xl my-4 mr-auto shadow-md w-full">
              <h3 class="font-semibold text-lg mb-1 {textColor(event.status)}">{event.title}</h3>
              {#if event.date}
              <p class="leading-tight text-justify w-full">
                {event.date}
              </p>
              {/if}
            </div>
          </div>          
        {/each}
      </div>
    </div>
  </div>
</div>