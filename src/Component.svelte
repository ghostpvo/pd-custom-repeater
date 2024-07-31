<script>
  import { getContext } from "svelte"

  export let data
  export let id
  export let title
  export let desciption
  export let label1
  export let additional1
  export let label2
  export let additional2
  export let label3
  export let additional3
  export let label4
  export let additional4

  const arrow = '<svg version="1.1" width="15" height="15" viewBox="0 0 512 512" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path d="M383.6,322.7L278.6,423c-5.8,6-13.7,9-22.4,9c-8.7,0-16.5-3-22.4-9L128.4,322.7c-12.5-11.9-12.5-31.3,0-43.2  c12.5-11.9,32.7-11.9,45.2,0l50.4,48.2v-217c0-16.9,14.3-30.6,32-30.6c17.7,0,32,13.7,32,30.6v217l50.4-48.2  c12.5-11.9,32.7-11.9,45.2,0C396.1,291.4,396.1,310.7,383.6,322.7z" fill="currentColor"/></svg>'

  const { styleable } = getContext("sdk")
  const component = getContext("component")

// SORTING SECTION
// ---
  // Sorting order and active column info
  $: sortingStatus = {
    order: "ASC",
    sortedBy: "last_edit",
  }

  // Sorting function
  const sortBy = sortingSource => {
    let sortBy = sortingSource

    // Custom field detecting
    if (sortingSource === 'specialRiskValue') {
      sortBy = 'value'
    }

    // Custom field detecting
    if (sortingSource === 'specialDateTime') {
      sortBy = 'last_edit'
    }

    if (sortingStatus.order === "ASC") {
      repeaterData.sort((a, b) => {
        if (a[sortBy] < b[sortBy]) return -1;
        if (a[sortBy] > b[sortBy]) return 1;
        return 0;
      });
      sortingStatus.order = "DESC";
    } else {
      repeaterData.sort((a, b) => {
        if (a[sortBy] < b[sortBy]) return 1;
        if (a[sortBy] > b[sortBy]) return -1;
        return 0;
      });
      sortingStatus.order = "ASC";
    }

    sortingStatus.sortedBy = sortingSource
    repeaterData = [...repeaterData]
  }
// ---
// END SORTING SECTION

// CUSTOM FIELDS SECTION
  // Adding of a value field, which does not come from Budibase
  const initialData = data.value.map(i => {
    return {
      ...i,
      value: i.Likelihood * i.Impact
    };
  });

  $: repeaterData = initialData;
  // Expected keys:
  // 'specialRiskValue': Computed field by "likelihood" and "Impact" values and colored by priority
  // 'specialDateTime': UI friendly parsed Date (YYYY.MM.DD HH:mm)
  const fieldParser = function (value, key) {
    if (key === "specialRiskValue") {
      return specialRiskValueBuilder(value, 'html')
    } else if (key === "specialDateTime") {
      return specialDateTimeBuilder(value)
    } else {
      return value[key] ? value[key] : '-'
    }
  }

  const specialRiskValueBuilder = function (value, view) {
    let riskValue = value.Impact * value.Likelihood
    let bgColor;

    const detectScore = (value) => {
      if (value < 4 && value > 0) {
        bgColor = '#2eb85c';
      } else if (value > 3 && value <=7) {
        bgColor = '#f8b114';
      } else if (value > 7) {
        bgColor = '#e45353';
      } else if (!value) {
        bgColor = '#CED4DA'
      }
    };

    detectScore(riskValue);

    const htmlResult = '<div style="display: inline-block; width: 60px; line-height: 30px;' +
      'text-align: center;' + 
      'color: #fff;' +
      'border-radius: 4px;' +
      'background-color: ' + bgColor +
    ';">' + riskValue + '</div>'

    return view === 'html' ? htmlResult : riskValue
  }

  const specialDateTimeBuilder = function (value) {
    const dateString = value.last_edit

    const [datePart, timePart] = dateString.split("T")
    let [year, month, day] = datePart.split("-").map(String)
    let [hours, minutes] = timePart.split(":").map(String)

    day = day.length < 2 ? "0" + day : day
    month = month.length < 2 ? "0" + month : month

    return `${day}.${month}.${year} ${hours}:${minutes}`
  }
// END CUSTOM FIELDS SECTION

// ACTIONS
  // Link to item card page
  const moveToCard = function (id) {
    const targetUrl = window.location.href + `/${id}`
    window.location.href = targetUrl
  }
// END ACTIONS
</script>

<div use:styleable={$component.styles}>
  <ul class="data-list">
    <li class="data-item data-item-header sorting-row {sortingStatus.order === "ASC" ? 'sorted-by-asc' : 'sorted-by-desc'}">
      {#if id}
        <span class="data-column data-column-general">
          <button class="sorting-item {sortingStatus.sortedBy === id ? 'is-active' : ''}" on:click={sortBy(id)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional1}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional1 ? 'is-active' : ''}" on:click={sortBy(additional1)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional2}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional2 ? 'is-active' : ''}" on:click={sortBy(additional2)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional3}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional3 ? 'is-active' : ''}" on:click={sortBy(additional3)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
      {#if additional4}
        <span class="data-column">
          <button class="sorting-item {sortingStatus.sortedBy === additional4 ? 'is-active' : ''}" on:click={sortBy(additional4)}>
            <i class="sorting-arrow">{ @html arrow }</i>
            <span>Sort by</span>
          </button>
        </span>
      {/if}
    </li>
    {#each repeaterData as item, index}
      <li
        class="data-item"
        on:click={moveToCard(item.id)}
        on:keydown={(event) => moveToCard(event, item.id)}
      >
        <div class="data-column data-column-general">
          <strong class="data-column-label">#{item[id]}</strong>
          {#if item[title]}
            <h5 class="data-item-title">{item[title]}</h5>
          {/if}
          <span class="data-column-data">{item[desciption]}</span>
        </div>
        {#if additional1}
          <div class="data-column">
            <strong class="data-column-label">{label1}</strong>
            <span class="data-column-data">{fieldParser(item, additional1, index)}</span>
          </div>
        {/if}
        {#if additional2}
          <div class="data-column">
            <strong class="data-column-label">{label2}</strong>
            <span class="data-column-data">{@html fieldParser(item, additional2, index)}</span>
          </div>
        {/if}
        {#if additional3}
          <div class="data-column">
            <strong class="data-column-label">{label3}</strong>
            <span class="data-column-data">{fieldParser(item, additional3, index)}</span>
          </div>
        {/if}
        {#if additional4}
          <div class="data-column">
            <strong class="data-column-label">{label4}</strong>
            <span class="data-column-data">{fieldParser(item, additional4, index)}</span>
          </div>
        {/if}
      </li>
    {/each}
  </ul>
</div>

<style>
  .sorting-item {
    display: flex;
    align-items: center;
    padding: 1px 17px 1px 3px;
    font-size: 12px;
    font-weight: 700;
    color: #6e6e6e;
    white-space: nowrap;
    border: 2px solid #6e6e6e;
    border-radius: 12px;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .sorting-item span {
    display: inline-block;
    vertical-align: middle;
    font-weight: 700;
    line-height: 16px;
  }

  .sorting-item:hover,
  .sorting-item.is-active {
    color: #fff;
    background-color: #6e6e6e;
  }

  .sorting-row .sorting-arrow {
    display: inline-block;
    vertical-align: middle;
    visibility: hidden;
  }

  .sorting-row.sorted-by-asc .sorting-arrow {
    transform: rotate(180deg);
  }

  .sorting-item.is-active .sorting-arrow {
    visibility: visible;
  }

  .data-list {
    display: table;
    width: 100%;
    padding-left: 0;
    border-spacing: 0 10px;
    list-style: none;
  }

  .data-list .data-item {
    display: table-row;
    padding: 16px;
    margin-top: 12px;
    background: #fff;
    box-shadow:
      rgba(0, 0, 0, 0.1) 0px 1px 3px 0px,
      rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
    box-sizing: border-box;
    cursor: pointer;
  }

  .data-list .data-item-header {
    cursor: default;
    box-shadow: none;
    background-color: transparent;
  }

  .data-list .data-column {
    display: table-cell;
    padding: 16px;
  }

  .data-list .data-column-label {
    display: block;
    font-weight: 700;
  }

  .data-list .data-item-title {
    margin: 10px 0 0;
    font-weight: 700;
    font-size: 18px;
  }

  .data-list .data-column-data {
    display: block;
    margin-top: 10px;
    font-size: 16px;
  }
</style>
