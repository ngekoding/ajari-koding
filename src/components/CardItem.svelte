<script>
  import Icon from "./Icon.svelte";
  import Tags from "./Tags.svelte";
  import Rating from "./Rating.svelte";
  export let item;

  const topic_tags = [...item.topic_tags];
</script>

<style>
  .card {
    height: 100%;
  }
  .card .card-body {
    padding-bottom: calc(1rem + 38px); /* card body padding + button height */
  }
  .card .btn--visit {
    position: absolute;
    bottom: 1rem;
  }
  .business-model {
    font-size: 10px;
  }
</style>

<div class="col-md-4 col-sm-6 col-xs-12">
  <div class="card">
    <div class="card-body">
      <small class="text-muted text-uppercase business-model">
        {item.business_model}
      </small>
      <h5 class="card-title font-weight-bold">{item.title}</h5>
      <h6 class="card-subtitle mb-2 text-muted">{item.creator}</h6>
      <p class="card-text mt-3">{item.description}</p>

      <Rating rating={item.rating} />

      {#if item.topic_tags && item.topic_tags.length > 0}
        <Tags title={item.title} topic_tags={item.topic_tags} />
      {/if}

      <a
        href="{item.url}?utm_source=ajari-koding&utm_medium=website&utm_campaign=phpid"
        target="_blank"
        rel="noopener noreferrer"
        class="btn btn-outline-primary btn--visit">
        Kunjungi
        <Icon name="arrow" width=24 height=24 />
      </a>
    </div>
  </div>
</div>
