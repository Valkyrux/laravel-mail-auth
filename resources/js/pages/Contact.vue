<template>
  
<div class="container">
  <div class="row">
    <div class="col">
      <form>
        <div class="mb-3">
            <label for="inputName" class="form-label">Nome</label>
          <input type="text" class="form-control" id="inputName" aria-describedby="nameHelp">
          <div id="nameHelp" class="form-text">Dimmi come ti chiami</div>
        </div>
        
        <div class="mb-3">
          <label for="inputEmail" class="form-label">Indirizzo e-mail</label>
          <input type="email" class="form-control" id="inputEmail" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">Questo indirizzo non verr&agrave; condiviso con nessun altro.</div>
        </div>
          
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
              
        <div class="mb-3 form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1">
          <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>

        <button type="submit" class="btn btn-primary">Submit</button>
      </form>
    </div>
  </div>
</div>

</template>

<script>
export default {
    name: 'Contact',
}
</script>

<style>

</style>