<script context="module">
    export const prerender = true;
</script>

<script>
    import Counter from '$lib/Counter.svelte';
    import {onMount} from "svelte";

    let someState = "Loading ..."

    // const res = async () => {
    // 	const res = await fetch(`http://localhost/api/something `, {
    // 		method: 'GET',
    // 		headers: {
    // 			'content-type': 'application/json'
    // 		},
    // 		// body: {}
    // 	});
    // 	return res.json();
    // }
    // export const testdata = res()

    let data = []

    function loadData() {
        return async function () {
            someState = "Loading 2...."
            // const url = `https://jsonplaceholder.typicode.com/posts`
            // const res = await fetch(url, {
            // 	method: 'GET',
            // 	headers: {
            // 		'content-type': 'application/json'
            // 	},
            // });
            // data = await res.json();
            // console.log(data)

            const url = `http://localhost/api/rating/history`
            // const res = await fetch(url, {
            // 	method: 'POST',
            // 	headers: {
            // 		'content-type': 'application/json'
            // 	},
            // 	body: JSON.stringify({
            // 		"rating_for_emp_id": "101557"
            // 	})
            // });
            // data = await res.json();
            // console.log(data)
            someState = "Loaded! Yay!"
        };
    }

    onMount(loadData())

    $: {
        console.log("some state changed : " + someState)
    }

    $: {
        console.log("data updated : " + data.length)
    }
</script>

<svelte:head>
    <title>Home</title>
</svelte:head>

<section>
    <h1>
        <div class="welcome">
            <picture>
                <source srcset="svelte-welcome.webp" type="image/webp"/>
                <img src="svelte-welcome.png" alt="Welcome"/>
            </picture>
        </div>

        to your new<br/>SvelteKit app
    </h1>

    <h2>
        try editing <strong>src/routes/index.svelte</strong>
    </h2>

    <Counter/>

    <form class="w-full max-w-lg">
        <div class="flex flex-wrap -mx-3 mb-6">
            <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                <label class="trimmed text-xs font-bold mb-2" for="grid-first-name">
                    First Name
                </label>
                <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="grid-first-name" type="text" placeholder="Jane">
                <p class="text-red-500 text-xs italic">Please fill out this field.</p>
            </div>
            <div class="w-full md:w-1/2 px-3">
                <label class="trimmed text-xs font-bold mb-2" for="grid-last-name">
                    Last Name
                </label>
                <input class="inputclass leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-last-name" type="text" placeholder="Doe">
            </div>
        </div>
        <div class="flex flex-wrap -mx-3 mb-6 bg-red-100">
            <div class="w-full px-3 ">
                <label class="trimmed text-xs font-bold mb-2" for="grid-password">
                    Password
                </label>
                <input class="inputclass mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-password" type="password" placeholder="******************">
                <p class="text-gray-600 text-xs italic">Make it as long and as crazy as you'd like</p>
            </div>
        </div>
        <div class="flex flex-wrap -mx-3 mb-2">
            <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
                <label class="block uppercase text-gray-700 text-xs font-bold mb-2" for="grid-city">
                    City
                </label>
                <input class="inputclass leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-city" type="text" placeholder="Albuquerque">
            </div>
            <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
                <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-state">
                    State
                </label>
                <div class="relative">
                    <select class="block appearance-none w-full bg-gray-200 border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-state">
                        <option>New Mexico</option>
                        <option>Missouri</option>
                        <option>Texas</option>
                    </select>
                    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700">
                        <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                    </div>
                </div>
            </div>
            <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
                <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-zip">
                    Zip
                </label>
                <input class="inputclass leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-zip" type="text" placeholder="90210">
            </div>
        </div>
        <div class="-mx-3 flex justify-center bg-green-100">
            <button class="px-8 py-3 m-3 bg-blue-100 rounded justify-center">Submit</button>
            <button class="px-8 py-3 m-3 bg-red-100 rounded hover:bg-green-300 justify-center">Cancel</button>
        </div>
    </form>

    <div class="grid grid-cols-3 gap-4">
        <div>One</div>
        <div>1.1</div>
        <div class="grid-flow-row">Two</div>
    </div>

    <div class="grid grid-cols-3 gap-4 justify-center content-center bg-red-100 p-5 text-center rounded">
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div class="col-span-3 bg-red-200 w-full rounded px-3 py-5">XSSSSsSSSSSSSSSSSSSSSSSSSSSSSSS</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <!-- ... -->
        <div>9</div>
    </div>

    <div class="grid grid-cols-6 bg-purple-100 text-center border border-black-500">
        <div class="text-center ">X</div>
        <div class="col-start-2 col-span-4 ... border border-green-900">1</div>
        <div class="col-start-1 col-end-3 bg-purple-200 ...">2</div>
        <div class="col-end-7 col-span-2 bg-purple-100 ... border border-green-900">3</div>
        <div class="col-start-1 col-end-7 bg-purple-300 text-center ...">4</div>
    </div>

    <button class="bg-blue-500 hover:bg-blue-700 text-white hover:text-black font-bold py-2 my-5 px-4 rounded"
            on:click={loadData()}>Load once again!
    </button>
    <!--	<div class="bg-gray-300 w-full text-center p-10 font-bold text-gray-700 rounded auto">{someState}</div>-->
    <div class="flex items-center bg-blue-500 text-white text-md font-bold px-4 py-3" role="alert">
        <svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
            <path d="M12.432 0c1.34 0 2.01.912 2.01 1.957 0 1.305-1.164 2.512-2.679 2.512-1.269 0-2.009-.75-1.974-1.99C9.789 1.436 10.67 0 12.432 0zM8.309 20c-1.058 0-1.833-.652-1.093-3.524l1.214-5.092c.211-.814.246-1.141 0-1.141-.317 0-1.689.562-2.502 1.117l-.528-.88c2.572-2.186 5.531-3.467 6.801-3.467 1.057 0 1.233 1.273.705 3.23l-1.391 5.352c-.246.945-.141 1.271.106 1.271.317 0 1.357-.392 2.379-1.207l.6.814C12.098 19.02 9.365 20 8.309 20z"/>
        </svg>
        <p class="text-white text-md font-bold">{someState}</p>
    </div>

    <h2 class="bg-blue-200 text-center font-bold text-red rounded-full m-5 py-5 w-full">Results of the API call are
        below: </h2>
    {#each data as item }
        <div>
            <p> {item.itp_rating} </p>
            <!--			<p> {item.title} </p>-->
        </div>
    {/each}
</section>

<style>

    .trimmed {
        @apply block uppercase tracking-wide text-gray-700 ;
    }

    .inputclass {
        @apply appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 ;
    }

    section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        flex: 1;
    }

    h1 {
        width: 100%;
    }

    .welcome {
        position: relative;
        width: 100%;
        height: 0;
        padding: 0 0 calc(100% * 495 / 2048) 0;
    }

    .welcome img {
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        display: block;
    }
</style>
