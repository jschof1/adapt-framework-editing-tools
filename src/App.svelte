<script>
    // we write export let to say that this is a property
    // that means we can change it later!

const dummyObj = [
  {
    _parentId: 1,
  },
  {
    _parentId: 2,
  },
  {
    _parentId: 3,
  },
  {
    _parentId: 4,
  },
];

const updateThing = (objectKey, textToInsert) =>
  dummyObj.map((el, idx) => ({
    ...el,
    objectKey: `${textToInsert}${Math.ceil(idx / 2)}`,
  }));
  

// console.log(updatedThing('_parentId', 'blockTitle'));

const exportToJsonFile = jsonData => {
  let dataStr = JSON.stringify(jsonData);
  let dataUri =
    'data:application/json;charset=utf-8,' + encodeURIComponent(dataStr);

  let exportFileDefaultName = 'data.json';

  let linkElement = document.createElement('a');
  linkElement.setAttribute('href', dataUri);
  linkElement.setAttribute('download', exportFileDefaultName);
  linkElement.click();
}

	const json = [{
		"first" : 1
	}]

  let jsonInput = `...`
$: console.log(jsonInput)


  const handleClick = () => {
    jsonInput = updateThing
  };

  // const handleInput = (e) => {
  //   beltColor = e.target.value;
  // };
</script>
<h1> Insert component.js file below </h1>
<textarea bind:value="{jsonInput}"/>



<!-- <input type="text" on:input="{handleInput}" value="{beltColor}" /> -->
<!-- <input type="text" bind:value="{beltColor}" /> -->

<button id="convert" on:click={() => updateThing('_parentId', jsonInput)}> pair the id's </button>
<button id="download" on:click={() => exportToJsonFile(jsonInput)}>download the json</button>


<style>
	textarea { width: 100%; height: 200px; }


    h1 {
        font-family: Helvetica;
				font-weight: 200
    }
</style>