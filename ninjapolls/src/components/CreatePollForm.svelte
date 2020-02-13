<script>
  import { createEventDispatcher } from 'svelte';
  import Button from '../shared/Button.svelte';

  let dispatch = createEventDispatcher();
  let fields = { question: '', answerA: '', answerB: '' };
  let errors = { question: '', answerA: '', answerB: '' };
  let valid = false;

  const submitHandler = () => {
    valid = true;
    // question
    if (fields.question.trim().length < 5) {
      valid = false;
      errors.question = 'Question must be at least 5 chars long'
    } else {
      errors.question = ''
    }
    // answer A
    if (fields.answerA.trim().length < 1) {
      valid = false;
      errors.answerA = 'Answer A cannot be empty'
    } else {
      errors.answerA = ''
    }
    // answer B
    if (fields.answerB.trim().length < 1) {
      valid = false;
      errors.answerB = 'Answer B cannot be empty'
    } else {
      errors.answerB = ''
    }
    // add new poll
    if (valid) {
      let poll = {...fields, id: Math.random(), votesA: 0, votesB: 0};
      dispatch('add', poll);
    }
  }
</script>

<form on:submit|preventDefault={submitHandler}>
  <div class="form-field">
    <label for="question">Poll Question:</label>
    <input type="text" id="question" bind:value={fields.question}>
    <div class="error">{ errors.question }</div>
  </div>
  <div class="form-field">
    <label for="answer-a">Answer A value:</label>
    <input type="text" id="answer-a" bind:value={fields.answerA}>
    <div class="error">{ errors.answerA }</div>
  </div>
  <div class="form-field">
    <label for="answer-b">Answer B value:</label>
    <input type="text" id="answer-b" bind:value={fields.answerB}>
    <div class="error">{ errors.answerB }</div>
  </div>
  <Button>Add Poll</Button>
</form>

<style>
  form{
    width: 400px;
    margin: 0 auto;
    text-align: center;
  }
  .form-field{
    margin: 18px auto;
  }
  input{
    width: 100%;
    border-radius: 6px;
  }
  label{
    margin: 10px auto;
    text-align: left;
  }
  .error{
    font-weight: bold;
    font-size: 12px;
    color: #d91b42;
  }
</style>