<template>
  <component
    :is="tag"
    :type="tag === 'button' ? nativeType : ''"
    :disabled="disabled || loading"
    @click="handleClick"
    class="btn"
    :class="[
      {'btn-round': round},
      {'btn-block': block},
      {'btn-icon btn-fab': icon},
      {[`btn-${type}`]: type},
      {[`btn-${size}`]: size},
      {'btn-simple': simple},
      {'btn-link': link},
      {'disabled': disabled && tag !== 'button'}
    ]">
    <slot name="loading">
        <i v-if="current && unique === current" class="fas fa-check"></i>
      <!-- <i v-if="loading" class="fas fa-spinner fa-spin"></i> -->
      <i v-if="current && unique === current" class="fas fa-spinner fa-spin"></i>
    </slot>
    <slot></slot>
  </component>
</template>
<script>
export default {
  name: "base-button",
  props: {
    tag: {
      type: String,
      default: "button",
      description: "Button html tag"
    },
    round: Boolean,
    icon: Boolean,
    block: Boolean,
    loading: Boolean,
    disabled: Boolean,
    type: {
      type: String,
      default: "default",
      description: "Button type (primary|secondary|danger etc)"
    },
    nativeType: {
      type: String,
      default: "button",
      description: "Button native type (e.g button, input etc)"
    },
    size: {
      type: String,
      default: "",
      description: "Button size (sm|lg)"
    },
    simple: {
      type: Boolean,
      description: "Whether button is simple (outlined)"
    },
    link: {
      type: Boolean,
      description: "Whether button is a link (no borders or background)"
    },

    unique:{
        type:String,
        default: ""
    },
    current:{

        type:String,
        default: ""

    }
    
  },
  methods: {
    handleClick(evt) {
      this.$emit("click", evt);
    }
  }
};
</script>
<style>



.btn
{
    font-size: 1rem;
    font-weight: 600;
    line-height: 1.5;

    display: inline-block;

    padding: .625rem 1.25rem;

    -webkit-user-select: none;
       -moz-user-select: none;
        -ms-user-select: none;
            user-select: none;
    transition: color .15s ease-in-out, background-color .15s ease-in-out, border-color .15s ease-in-out, box-shadow .15s ease-in-out; 
    text-align: center;
    vertical-align: middle;
    white-space: nowrap;

    border: 1px solid transparent;
    border-radius: .25rem;
}


.btn.btn-round {
  border-radius: 30px;
}

.btn.btn-fab,
.btn.btn-just-icon {
  font-size: 24px;
  height: 41px;
  min-width: 41px;
  width: 41px;
  padding: 0;
  overflow: hidden;
  position: relative;
  line-height: 41px;
}

.btn.btn-fab.btn-round,
.btn.btn-just-icon.btn-round {
  border-radius: 50%;
}

@media screen and (prefers-reduced-motion: reduce)
{
    .btn
    {
        transition: none;
    }
}
.btn:hover,
.btn:focus
{
    text-decoration: none;
}
.btn:focus,
.btn.focus
{
    outline: 0;
    box-shadow: 0 7px 14px rgba(50, 50, 93, .1), 0 3px 6px rgba(0, 0, 0, .08);
}
.btn.disabled,
.btn:disabled
{
    opacity: .65;
    box-shadow: none;
}
.btn:not(:disabled):not(.disabled)
{
    cursor: pointer;
}
.btn:not(:disabled):not(.disabled):active,
.btn:not(:disabled):not(.disabled).active
{
    box-shadow: none;
}
.btn:not(:disabled):not(.disabled):active:focus,
.btn:not(:disabled):not(.disabled).active:focus
{
    box-shadow: 0 7px 14px rgba(50, 50, 93, .1), 0 3px 6px rgba(0, 0, 0, .08), none;
}

a.btn.disabled,
fieldset:disabled a.btn
{
    pointer-events: none;
}

.btn-primary
{
    color: #fff;
    border-color: #5e72e4;
    background-color: #5e72e4;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-primary:hover
{
    color: #fff;
    border-color: #5e72e4; 
    background-color: #5e72e4;
}
.btn-primary:focus,
.btn-primary.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(94, 114, 228, .5);
}
.btn-primary.disabled,
.btn-primary:disabled
{
    color: #fff;
    border-color: #5e72e4; 
    background-color: #5e72e4;
}
.btn-primary:not(:disabled):not(.disabled):active,
.btn-primary:not(:disabled):not(.disabled).active,
.show > .btn-primary.dropdown-toggle
{
    color: #fff;
    border-color: #5e72e4; 
    background-color: #324cdd;
}
.btn-primary:not(:disabled):not(.disabled):active:focus,
.btn-primary:not(:disabled):not(.disabled).active:focus,
.show > .btn-primary.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(94, 114, 228, .5);
}

.btn-secondary
{
    color: #212529;
    border-color: #f4f5f7;
    background-color: #f4f5f7;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-secondary:hover
{
    color: #212529;
    border-color: #f4f5f7; 
    background-color: #f4f5f7;
}
.btn-secondary:focus,
.btn-secondary.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(244, 245, 247, .5);
}
.btn-secondary.disabled,
.btn-secondary:disabled
{
    color: #212529;
    border-color: #f4f5f7; 
    background-color: #f4f5f7;
}
.btn-secondary:not(:disabled):not(.disabled):active,
.btn-secondary:not(:disabled):not(.disabled).active,
.show > .btn-secondary.dropdown-toggle
{
    color: #212529;
    border-color: #f4f5f7; 
    background-color: #d6dae2;
}
.btn-secondary:not(:disabled):not(.disabled):active:focus,
.btn-secondary:not(:disabled):not(.disabled).active:focus,
.show > .btn-secondary.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(244, 245, 247, .5);
}

.btn-success
{
    color: #fff;
    border-color: #2dce89;
    background-color: #2dce89;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-success:hover
{
    color: #fff;
    border-color: #2dce89; 
    background-color: #2dce89;
}
.btn-success:focus,
.btn-success.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(45, 206, 137, .5);
}
.btn-success.disabled,
.btn-success:disabled
{
    color: #fff;
    border-color: #2dce89; 
    background-color: #2dce89;
}
.btn-success:not(:disabled):not(.disabled):active,
.btn-success:not(:disabled):not(.disabled).active,
.show > .btn-success.dropdown-toggle
{
    color: #fff;
    border-color: #2dce89; 
    background-color: #24a46d;
}
.btn-success:not(:disabled):not(.disabled):active:focus,
.btn-success:not(:disabled):not(.disabled).active:focus,
.show > .btn-success.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(45, 206, 137, .5);
}

.btn-info
{
    color: #fff;
    border-color: #11cdef;
    background-color: #11cdef;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-info:hover
{
    color: #fff;
    border-color: #11cdef; 
    background-color: #11cdef;
}
.btn-info:focus,
.btn-info.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(17, 205, 239, .5);
}
.btn-info.disabled,
.btn-info:disabled
{
    color: #fff;
    border-color: #11cdef; 
    background-color: #11cdef;
}
.btn-info:not(:disabled):not(.disabled):active,
.btn-info:not(:disabled):not(.disabled).active,
.show > .btn-info.dropdown-toggle
{
    color: #fff;
    border-color: #11cdef; 
    background-color: #0da5c0;
}
.btn-info:not(:disabled):not(.disabled):active:focus,
.btn-info:not(:disabled):not(.disabled).active:focus,
.show > .btn-info.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(17, 205, 239, .5);
}

.btn-warning
{
    color: #fff;
    border-color: #fb6340;
    background-color: #fb6340;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-warning:hover
{
    color: #fff;
    border-color: #fb6340; 
    background-color: #fb6340;
}
.btn-warning:focus,
.btn-warning.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(251, 99, 64, .5);
}
.btn-warning.disabled,
.btn-warning:disabled
{
    color: #fff;
    border-color: #fb6340; 
    background-color: #fb6340;
}
.btn-warning:not(:disabled):not(.disabled):active,
.btn-warning:not(:disabled):not(.disabled).active,
.show > .btn-warning.dropdown-toggle
{
    color: #fff;
    border-color: #fb6340; 
    background-color: #fa3a0e;
}
.btn-warning:not(:disabled):not(.disabled):active:focus,
.btn-warning:not(:disabled):not(.disabled).active:focus,
.show > .btn-warning.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(251, 99, 64, .5);
}

.btn-danger
{
    color: #fff;
    border-color: #f5365c;
    background-color: #f5365c;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-danger:hover
{
    color: #fff;
    border-color: #f5365c; 
    background-color: #f5365c;
}
.btn-danger:focus,
.btn-danger.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(245, 54, 92, .5);
}
.btn-danger.disabled,
.btn-danger:disabled
{
    color: #fff;
    border-color: #f5365c; 
    background-color: #f5365c;
}
.btn-danger:not(:disabled):not(.disabled):active,
.btn-danger:not(:disabled):not(.disabled).active,
.show > .btn-danger.dropdown-toggle
{
    color: #fff;
    border-color: #f5365c; 
    background-color: #ec0c38;
}
.btn-danger:not(:disabled):not(.disabled):active:focus,
.btn-danger:not(:disabled):not(.disabled).active:focus,
.show > .btn-danger.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(245, 54, 92, .5);
}

.btn-light
{
    color: #fff;
    border-color: #adb5bd;
    background-color: #adb5bd;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-light:hover
{
    color: #fff;
    border-color: #adb5bd; 
    background-color: #adb5bd;
}
.btn-light:focus,
.btn-light.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(173, 181, 189, .5);
}
.btn-light.disabled,
.btn-light:disabled
{
    color: #fff;
    border-color: #adb5bd; 
    background-color: #adb5bd;
}
.btn-light:not(:disabled):not(.disabled):active,
.btn-light:not(:disabled):not(.disabled).active,
.show > .btn-light.dropdown-toggle
{
    color: #fff;
    border-color: #adb5bd; 
    background-color: #919ca6;
}
.btn-light:not(:disabled):not(.disabled):active:focus,
.btn-light:not(:disabled):not(.disabled).active:focus,
.show > .btn-light.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(173, 181, 189, .5);
}

.btn-dark
{
    color: #fff;
    border-color: #212529;
    background-color: #212529;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-dark:hover
{
    color: #fff;
    border-color: #212529; 
    background-color: #212529;
}
.btn-dark:focus,
.btn-dark.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(33, 37, 41, .5);
}
.btn-dark.disabled,
.btn-dark:disabled
{
    color: #fff;
    border-color: #212529; 
    background-color: #212529;
}
.btn-dark:not(:disabled):not(.disabled):active,
.btn-dark:not(:disabled):not(.disabled).active,
.show > .btn-dark.dropdown-toggle
{
    color: #fff;
    border-color: #212529; 
    background-color: #0a0c0d;
}
.btn-dark:not(:disabled):not(.disabled):active:focus,
.btn-dark:not(:disabled):not(.disabled).active:focus,
.show > .btn-dark.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(33, 37, 41, .5);
}

.btn-default
{
    color: #fff;
    border-color: #172b4d;
    background-color: #172b4d;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-default:hover
{
    color: #fff;
    border-color: #172b4d; 
    background-color: #172b4d;
}
.btn-default:focus,
.btn-default.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(23, 43, 77, .5);
}
.btn-default.disabled,
.btn-default:disabled
{
    color: #fff;
    border-color: #172b4d; 
    background-color: #172b4d;
}
.btn-default:not(:disabled):not(.disabled):active,
.btn-default:not(:disabled):not(.disabled).active,
.show > .btn-default.dropdown-toggle
{
    color: #fff;
    border-color: #172b4d; 
    background-color: #0b1526;
}
.btn-default:not(:disabled):not(.disabled):active:focus,
.btn-default:not(:disabled):not(.disabled).active:focus,
.show > .btn-default.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(23, 43, 77, .5);
}

.btn-white
{
    color: #212529;
    border-color: #fff;
    background-color: #fff;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-white:hover
{
    color: #212529;
    border-color: white; 
    background-color: white;
}
.btn-white:focus,
.btn-white.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(255, 255, 255, .5);
}
.btn-white.disabled,
.btn-white:disabled
{
    color: #212529;
    border-color: #fff; 
    background-color: #fff;
}
.btn-white:not(:disabled):not(.disabled):active,
.btn-white:not(:disabled):not(.disabled).active,
.show > .btn-white.dropdown-toggle
{
    color: #212529;
    border-color: white; 
    background-color: #e6e6e6;
}
.btn-white:not(:disabled):not(.disabled):active:focus,
.btn-white:not(:disabled):not(.disabled).active:focus,
.show > .btn-white.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(255, 255, 255, .5);
}

.btn-neutral
{
    color: #212529;
    border-color: #fff;
    background-color: #fff;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-neutral:hover
{
    color: #212529;
    border-color: white; 
    background-color: white;
}
.btn-neutral:focus,
.btn-neutral.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(255, 255, 255, .5);
}
.btn-neutral.disabled,
.btn-neutral:disabled
{
    color: #212529;
    border-color: #fff; 
    background-color: #fff;
}
.btn-neutral:not(:disabled):not(.disabled):active,
.btn-neutral:not(:disabled):not(.disabled).active,
.show > .btn-neutral.dropdown-toggle
{
    color: #212529;
    border-color: white; 
    background-color: #e6e6e6;
}
.btn-neutral:not(:disabled):not(.disabled):active:focus,
.btn-neutral:not(:disabled):not(.disabled).active:focus,
.show > .btn-neutral.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(255, 255, 255, .5);
}

.btn-darker
{
    color: #fff;
    border-color: black;
    background-color: black;
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08);
}
.btn-darker:hover
{
    color: #fff;
    border-color: black; 
    background-color: black;
}
.btn-darker:focus,
.btn-darker.focus
{
    box-shadow: 0 4px 6px rgba(50, 50, 93, .11), 0 1px 3px rgba(0, 0, 0, .08), 0 0 0 0 rgba(0, 0, 0, .5);
}
.btn-darker.disabled,
.btn-darker:disabled
{
    color: #fff;
    border-color: black; 
    background-color: black;
}
.btn-darker:not(:disabled):not(.disabled):active,
.btn-darker:not(:disabled):not(.disabled).active,
.show > .btn-darker.dropdown-toggle
{
    color: #fff;
    border-color: black; 
    background-color: black;
}
.btn-darker:not(:disabled):not(.disabled):active:focus,
.btn-darker:not(:disabled):not(.disabled).active:focus,
.show > .btn-darker.dropdown-toggle:focus
{
    box-shadow: none, 0 0 0 0 rgba(0, 0, 0, .5);
}

.btn-outline-primary
{
    color: #5e72e4 !important;
    border-color: #5e72e4 !important; 
    background-color: transparent;
    background-image: none;
}
.btn-outline-primary:hover
{
    color: #fff !important;
    border-color: #5e72e4 !important; 
    background-color: #5e72e4 !important;
}
.btn-outline-primary:focus,
.btn-outline-primary.focus
{
    box-shadow: 0 0 0 0 rgba(94, 114, 228, .5) !important;
}
.btn-outline-primary.disabled,
.btn-outline-primary:disabled
{
    color: #5e72e4 !important;
    background-color: transparent !important;
}
.btn-outline-primary:not(:disabled):not(.disabled):active,
.btn-outline-primary:not(:disabled):not(.disabled).active,
.show > .btn-outline-primary.dropdown-toggle
{
    color: #fff !important;
    border-color: #5e72e4 !important; 
    background-color: #5e72e4 !important;
}
.btn-outline-primary:not(:disabled):not(.disabled):active:focus,
.btn-outline-primary:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-primary.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(94, 114, 228, .5) !important;
}

.btn-outline-secondary
{
    color: #f4f5f7 !important;
    border-color: #f4f5f7 !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-secondary:hover
{
    color: #212529 !important;
    border-color: #f4f5f7 !important; 
    background-color: #f4f5f7 !important;
}
.btn-outline-secondary:focus,
.btn-outline-secondary.focus
{
    box-shadow: 0 0 0 0 rgba(244, 245, 247, .5) !important;
}
.btn-outline-secondary.disabled,
.btn-outline-secondary:disabled
{
    color: #f4f5f7 !important;
    background-color: transparent !important;
}
.btn-outline-secondary:not(:disabled):not(.disabled):active,
.btn-outline-secondary:not(:disabled):not(.disabled).active,
.show > .btn-outline-secondary.dropdown-toggle
{
    color: #212529 !important;
    border-color: #f4f5f7 !important; 
    background-color: #f4f5f7 !important;
}
.btn-outline-secondary:not(:disabled):not(.disabled):active:focus,
.btn-outline-secondary:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-secondary.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(244, 245, 247, .5) !important;
}

.btn-outline-success
{
    color: #2dce89 !important;
    border-color: #2dce89 !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-success:hover
{
    color: #fff !important;
    border-color: #2dce89 !important; 
    background-color: #2dce89 !important;
}
.btn-outline-success:focus,
.btn-outline-success.focus
{
    box-shadow: 0 0 0 0 rgba(45, 206, 137, .5) !important;
}
.btn-outline-success.disabled,
.btn-outline-success:disabled
{
    color: #2dce89 !important;
    background-color: transparent !important;
}
.btn-outline-success:not(:disabled):not(.disabled):active,
.btn-outline-success:not(:disabled):not(.disabled).active,
.show > .btn-outline-success.dropdown-toggle
{
    color: #fff !important;
    border-color: #2dce89 !important; 
    background-color: #2dce89 !important;
}
.btn-outline-success:not(:disabled):not(.disabled):active:focus,
.btn-outline-success:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-success.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(45, 206, 137, .5) !important;
}

.btn-outline-info
{
    color: #11cdef !important;
    border-color: #11cdef !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-info:hover
{
    color: #fff !important;
    border-color: #11cdef !important;  
    background-color: #11cdef !important;
}
.btn-outline-info:focus,
.btn-outline-info.focus
{
    box-shadow: 0 0 0 0 rgba(17, 205, 239, .5) !important;
}
.btn-outline-info.disabled,
.btn-outline-info:disabled
{
    color: #11cdef !important;
    background-color: transparent !important;
}
.btn-outline-info:not(:disabled):not(.disabled):active,
.btn-outline-info:not(:disabled):not(.disabled).active,
.show > .btn-outline-info.dropdown-toggle
{
    color: #fff !important;
    border-color: #11cdef !important; 
    background-color: #11cdef !important;
}
.btn-outline-info:not(:disabled):not(.disabled):active:focus,
.btn-outline-info:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-info.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(17, 205, 239, .5) !important;
}

.btn-outline-warning
{
    color: #fb6340 !important;
    border-color: #fb6340 !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-warning:hover
{
    color: #fff !important;
    border-color: #fb6340 !important; 
    background-color: #fb6340 !important;
}
.btn-outline-warning:focus,
.btn-outline-warning.focus
{
    box-shadow: 0 0 0 0 rgba(251, 99, 64, .5) !important;
}
.btn-outline-warning.disabled,
.btn-outline-warning:disabled
{
    color: #fb6340 !important;
    background-color: transparent !important;
}
.btn-outline-warning:not(:disabled):not(.disabled):active,
.btn-outline-warning:not(:disabled):not(.disabled).active,
.show > .btn-outline-warning.dropdown-toggle
{
    color: #fff !important;
    border-color: #fb6340 !important; 
    background-color: #fb6340 !important;
}
.btn-outline-warning:not(:disabled):not(.disabled):active:focus,
.btn-outline-warning:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-warning.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(251, 99, 64, .5) !important;
}

.btn-outline-danger
{
    color: #f5365c !important;
    border-color: #f5365c !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-danger:hover
{
    color: #fff !important;
    border-color: #f5365c !important; 
    background-color: #f5365c !important;
}
.btn-outline-danger:focus,
.btn-outline-danger.focus
{
    box-shadow: 0 0 0 0 rgba(245, 54, 92, .5) !important;
}
.btn-outline-danger.disabled,
.btn-outline-danger:disabled
{
    color: #f5365c !important;
    background-color: transparent !important;
}
.btn-outline-danger:not(:disabled):not(.disabled):active,
.btn-outline-danger:not(:disabled):not(.disabled).active,
.show > .btn-outline-danger.dropdown-toggle
{
    color: #fff !important;
    border-color: #f5365c !important; 
    background-color: #f5365c !important;
}
.btn-outline-danger:not(:disabled):not(.disabled):active:focus,
.btn-outline-danger:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-danger.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(245, 54, 92, .5) !important;
}

.btn-outline-light
{
    color: #adb5bd !important;
    border-color: #adb5bd !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-light:hover
{
    color: #fff;
    border-color: #adb5bd; 
    background-color: #adb5bd;
}
.btn-outline-light:focus,
.btn-outline-light.focus
{
    box-shadow: 0 0 0 0 rgba(173, 181, 189, .5) !important;
}
.btn-outline-light.disabled,
.btn-outline-light:disabled
{
    color: #adb5bd !important;
    background-color: transparent !important;
}
.btn-outline-light:not(:disabled):not(.disabled):active,
.btn-outline-light:not(:disabled):not(.disabled).active,
.show > .btn-outline-light.dropdown-toggle
{
    color: #fff !important;
    border-color: #adb5bd !important; 
    background-color: #adb5bd !important;
}
.btn-outline-light:not(:disabled):not(.disabled):active:focus,
.btn-outline-light:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-light.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(173, 181, 189, .5) !important;
}

.btn-outline-dark
{
    color: #212529 !important;
    border-color: #212529 !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-dark:hover
{
    color: #fff !important;
    border-color: #212529 !important; 
    background-color: #212529 !important;
}
.btn-outline-dark:focus,
.btn-outline-dark.focus
{
    box-shadow: 0 0 0 0 rgba(33, 37, 41, .5) !important;
}
.btn-outline-dark.disabled,
.btn-outline-dark:disabled
{
    color: #212529 !important;
    background-color: transparent !important;
}
.btn-outline-dark:not(:disabled):not(.disabled):active,
.btn-outline-dark:not(:disabled):not(.disabled).active,
.show > .btn-outline-dark.dropdown-toggle
{
    color: #fff !important;
    border-color: #212529 !important; 
    background-color: #212529 !important;
}
.btn-outline-dark:not(:disabled):not(.disabled):active:focus,
.btn-outline-dark:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-dark.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(33, 37, 41, .5) !important;
}

.btn-outline-default
{
    color: #172b4d !important;
    border-color: #172b4d !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-default:hover
{
    color: #fff !important;
    border-color: #172b4d !important; 
    background-color: #172b4d !important;
}
.btn-outline-default:focus,
.btn-outline-default.focus
{
    box-shadow: 0 0 0 0 rgba(23, 43, 77, .5) !important;
}
.btn-outline-default.disabled,
.btn-outline-default:disabled
{
    color: #172b4d !important;
    background-color: transparent !important;
}
.btn-outline-default:not(:disabled):not(.disabled):active,
.btn-outline-default:not(:disabled):not(.disabled).active,
.show > .btn-outline-default.dropdown-toggle
{
    color: #fff !important;
    border-color: #172b4d !important; 
    background-color: #172b4d !important;
}
.btn-outline-default:not(:disabled):not(.disabled):active:focus,
.btn-outline-default:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-default.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(23, 43, 77, .5) !important;
}

.btn-outline-white
{
    color: #fff !important;
    border-color: #fff !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-white:hover
{
    color: #212529 !important;
    border-color: #fff !important; 
    background-color: #fff !important;
}
.btn-outline-white:focus,
.btn-outline-white.focus
{
    box-shadow: 0 0 0 0 rgba(255, 255, 255, .5) !important;
}
.btn-outline-white.disabled,
.btn-outline-white:disabled
{
    color: #fff !important;
    background-color: transparent !important;
}
.btn-outline-white:not(:disabled):not(.disabled):active,
.btn-outline-white:not(:disabled):not(.disabled).active,
.show > .btn-outline-white.dropdown-toggle
{
    color: #212529 !important;
    border-color: #fff !important;  
    background-color: #fff !important;
}
.btn-outline-white:not(:disabled):not(.disabled):active:focus,
.btn-outline-white:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-white.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(255, 255, 255, .5) !important;
}

.btn-outline-neutral
{
    color: #fff !important;
    border-color: #fff !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-neutral:hover
{
    color: #212529 !important;
    border-color: #fff !important; 
    background-color: #fff !important;
}
.btn-outline-neutral:focus,
.btn-outline-neutral.focus
{
    box-shadow: 0 0 0 0 rgba(255, 255, 255, .5) !important;
}
.btn-outline-neutral.disabled,
.btn-outline-neutral:disabled
{
    color: #fff !important;
    background-color: transparent !important;
}
.btn-outline-neutral:not(:disabled):not(.disabled):active,
.btn-outline-neutral:not(:disabled):not(.disabled).active,
.show > .btn-outline-neutral.dropdown-toggle
{
    color: #212529 !important;
    border-color: #fff !important; 
    background-color: #fff !important;
}
.btn-outline-neutral:not(:disabled):not(.disabled):active:focus,
.btn-outline-neutral:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-neutral.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(255, 255, 255, .5) !important;
}

.btn-outline-darker
{
    color: black !important;
    border-color: black !important; 
    background-color: transparent !important;
    background-image: none !important;
}
.btn-outline-darker:hover
{
    color: #fff !important;
    border-color: black !important; 
    background-color: black !important;
}
.btn-outline-darker:focus,
.btn-outline-darker.focus
{
    box-shadow: 0 0 0 0 rgba(0, 0, 0, .5) !important;
}
.btn-outline-darker.disabled,
.btn-outline-darker:disabled
{
    color: black !important;
    background-color: transparent !important;
}
.btn-outline-darker:not(:disabled):not(.disabled):active,
.btn-outline-darker:not(:disabled):not(.disabled).active,
.show > .btn-outline-darker.dropdown-toggle
{
    color: #fff !important;
    border-color: black !important; 
    background-color: black !important;
}
.btn-outline-darker:not(:disabled):not(.disabled):active:focus,
.btn-outline-darker:not(:disabled):not(.disabled).active:focus,
.show > .btn-outline-darker.dropdown-toggle:focus
{
    box-shadow: 0 0 0 0 rgba(0, 0, 0, .5) !important;
}

.btn-link
{
    font-weight: 400;

    color: #5e72e4 !important;
    background-color: transparent;
}
.btn-link:hover
{
    text-decoration: none;

    color: #233dd2 !important;

    border-color: transparent; 
    background-color: transparent;
}
.btn-link:focus,
.btn-link.focus
{
    text-decoration: none;

    border-color: transparent;
    box-shadow: none;
}
.btn-link:disabled,
.btn-link.disabled
{
    pointer-events: none; 

    color: #8898aa;
}

.btn-lg,
.btn-group-lg > .btn
{
    font-size: 1.25rem;
    line-height: 1.5;

    padding: .875rem 1rem;

    border-radius: .3rem;
}

.btn-sm,
.btn-group-sm > .btn
{
    font-size: .875rem;
    line-height: 1.5;

    padding: .25rem .5rem;

    border-radius: .25rem;
}

.btn-block
{
    display: block;

    width: 100%;
}
.btn-block + .btn-block
{
    margin-top: .5rem;
}



</style>
