<template>
  <form>
    <!-- Name -->
    <div class="field">
      <label class="label is-medium">Vardas</label>
      <div class="control has-icons-left">
        <input class="input is-medium" type="text" placeholder="Vardas Pavardė" />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="user" />
        </span>
      </div>
    </div>
    <!-- Email -->
    <div class="field">
      <label class="label is-medium">El. paštas</label>
      <div class="control has-icons-left">
        <input
          class="input is-medium"
          type="email"
          placeholder="as@email.com"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="envelope" />
        </span>
      </div>
    </div>
    <!-- Subject -->
    <div class="field">
      <label class="label is-medium">Tema</label>
      <div class="control has-icons-left">
        <input
          class="input is-medium"
          type="text"
          placeholder="Tema"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="briefcase" />
        </span>
      </div>
    </div>
    <!-- Message -->
    <div class="field">
      <label class="label is-medium">Žinutė</label>
      <div class="control">
        <textarea
          class="textarea"
          placeholder="Jūsų klausimas"
          rows="8"
        ></textarea>
      </div>
    </div>
    <div class="control">
      <button class="button is-primary">
        Siųsti
      </button>
    </div>
  </form>
</template>
