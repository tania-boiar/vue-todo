<script>
import todos from './todos';

export default {
  data() {
    return {
      todos,
    }
  }
}
</script>

<template>
    <div class="todoapp">
      <h1 class="todoapp__title">todos</h1>

      <div class="todoapp__content">
        <header class="todoapp__header">
          <button type="button" class="todoapp__toggle-all active" />

          <form>
            <input
              type="text"
              class="todoapp__new-todo"
              placeholder="What needs to be done?"
            />
          </form>
        </header>

        <section class="todoapp__main">
          <div
          v-for="todo of todos"
          :key="todo.id"
          class="todo"
          :class="{ completed: todo.completed }"
          >
            <label class="todo__status-label">
              <input
                type="checkbox"
                class="todo__status"
                :checked="todo.completed"
              />
            </label>

            <span class="todo__title">{{ todo.title }}</span>

            <button type="button" class="todo__remove">×</button>

            <div class="modal overlay" :class="{'is-active': false}">
              <div class="modal-background has-background-white-ter" />
              <div class="loader" />
            </div>
          </div>

          <div class="todo">
            <label class="todo__status-label">
              <input
                type="checkbox"
                class="todo__status"
              />
            </label>

            <form>
              <input
                type="text"
                class="todo__title-field"
                placeholder="Empty todo will be deleted"
                value="Todo is being edited now"
              />
            </form>

            <div class="modal overlay">
              <div class="modal-background has-background-white-ter" />
              <div class="loader" />
            </div>
          </div>

        </section>

        <footer class="todoapp__footer">
          <span class="todo-count">
            3 items left
          </span>

          <nav class="filter">
            <a href="#/" class="filter__link selected">
              All
            </a>

            <a href="#/active" class="filter__link">
              Active
            </a>

            <a href="#/completed" class="filter__link">
              Completed
            </a>
          </nav>

          <button type="button" class="todoapp__clear-completed">
            Clear completed
          </button>
        </footer>
      </div>

      <div class="notification is-danger is-light has-text-weight-normal">
        <button type="button" class="delete" />

        Unable to add a todo
        <br />
        Unable to delete a todo
        <br />
        Unable to update a todo
      </div>
    </div>
</template>