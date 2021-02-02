<script>
  import { FaUser, FaChevronRight } from 'svelte-icons/fa';
</script>

<div class="user-logout">
  <div class="content">
    <div class="user-data">
      <span class="icon"><FaUser /></span>
      <span class="user">Billy Paredes Aycho</span>
    </div>
    <span class="icon hide"><FaChevronRight /></span>
  </div>
</div>

<style lang="scss">
  .user-logout {
    width: 100%;
    height: 100%;
    padding: 1em;
    box-sizing: border-box;
    cursor: pointer;

    .content {
      padding: 12px .8em;
      box-sizing: border-box;
      border-radius: 15px;
      background-color: var(--color-primary-light);
      justify-content: space-around;
      
      & , .user-data {
        display: flex;
        align-items: center;
      }

      .icon , .user {
        transition: .3s;
      }

      .icon {
        width: 16px;
        height: 16px;
        display: inline-block;

        &.hide {
          visibility: hidden;
        }
      }

      .user {
        padding-left: 1em;
        font-size: .9em;
        font-weight: bold;
      }
    }

    &:hover .content {
      .icon , .user {
        color: #fff;
      }

      .icon.hide {
        visibility: visible;
      }
    }
  }
</style>