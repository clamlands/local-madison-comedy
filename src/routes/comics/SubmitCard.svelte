<script>
  export let submitUrl = "#";
</script>

<div class="submit-card">
  <div class="content">
    <h3>Are you a Madison comic?</h3>
    <p>Missing from this page? Submit your information to join the directory!</p>
    <a href={submitUrl} target="_blank" rel="noreferrer" class="submit-button">
      Submit Your Info
    </a>
  </div>
</div>

<style>
  .submit-card {
    background: rgba(255, 255, 255, 0.1);
    border: 2px dashed var(--neon);
    border-radius: 8px;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 20px;
    transition: all 0.3s ease;
  }

  .submit-card:hover {
    background: rgba(255, 255, 255, 0.15);
    box-shadow: 0 0 15px rgba(var(--neon), 0.3);
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: 15px;
    align-items: center;
  }

  h3 {
    color: var(--neon);
    margin: 0;
  }

  p {
    margin: 0;
    opacity: 0.9;
  }

  .submit-button {
    background: var(--neon);
    color: black;
    padding: 10px 20px;
    border-radius: 4px;
    text-decoration: none;
    font-weight: bold;
    transition: all 0.2s ease;
  }

  .submit-button:hover {
    transform: scale(1.05);
    box-shadow: 0 0 10px var(--neon);
  }
</style>