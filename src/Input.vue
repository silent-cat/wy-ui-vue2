<template>
  <!-- <div class="wy-input-wrapper" :class="{ error }"> -->
  <div class="wy-input-wrapper">
    <label>
      <input
        :value="value"
        :disabled="disabled"
        :readonly="readonly"
        :placeholder="placeholder"
        :type="type"
        @input="$emit('input', $event.target.value)"
        @focus="$emit('focus', $event.target.value)"
        @blur="$emit('blur', $event.target.value)"
      />
      <!-- <template v-if="error">
        <Icon class="wy-icon-error" name="error"></Icon>
        <span class="wy-error-message">{{ error }}</span>
      </template> -->
    </label>
  </div>
</template>

<script>
import Icon from './Icon'

export default {
  components: { Icon },
  props: {
    value: {
      type: String
    },
    disabled: {
      type: Boolean,
      default: false
    },
    readonly: {
      type: Boolean,
      default: false
    },
    // error: {
    //   type: String
    // },
    placeholder: {
      type: String
    },
    type: {
      type: String,
      default: 'text'
    }
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
$height: 42px;
$border-color: #686868;
$border-color-hover: #409eff;
$border-radius: 4px;
$font-size: 14px;
$red: #f1453d;
.wy-input-wrapper {
  font-size: $font-size;
  display: inline-block;
  align-items: center;

  > label {
    > :not(:last-child) {
      margin-right: 0.5em;
    }

    > input {
      height: $height;
      border: 2px solid #fff;
      border-radius: 4px;
      padding: 0 8px;
      font-size: inherit;
      box-shadow: 2px 2px 6px rgba(0, 0, 0, 0.3),
        inset 2px 2px 6px rgba(0, 0, 0, 0.2);
      transition: all 250ms;

      &:hover {
      }
      &:focus {
        outline: none;
      }

      &[disabled] {
        color: #bbb;
        cursor: not-allowed;
      }
      &[readonly] {
        cursor: not-allowed;
      }
    }
  }

  /* &.error {
    > label {
      > input {
        border-color: $red;
      }

      .wy-icon-error {
        fill: $red;
      }

      .wy-error-message {
        color: $red;
      }
    }
  } */
}
</style>
