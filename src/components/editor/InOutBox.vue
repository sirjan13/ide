<template>
  <div id="inoutbox" class="fsHide" v-show="this.$store.state.showInOutBox">
    <div class="panel-input panel-default">
      <div class="panel-heading">Input</div>
      <div class="panel-body">
        <textarea class="textbox" id="test-input" rows="2"
                  placeholder="Enter your custom inputs" :value="this.$store.state.customInput"
                  @change="customInputChange"></textarea>
      </div>
    </div>
    <div class="panel-output panel-default">
      <div class="panel-heading">Output</div>
      <div class="panel-body">
       <pre id="output">{{this.$store.state.output}}</pre>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'inoutbox',
    methods: {
      customInputChange(e) {
        this.$store.commit('changeCustomInput', e.target.value)
      }
    }
  }
</script>

<style scoped>
  #inoutbox {
    position: fixed;
    width: 100vw;
    bottom: 0;
    left: 0;
    z-index: 20;
  }

  #output, #test-input {
    width: calc(50vw - 7px);
    border-radius: 0 !important;
    margin: 0;
    height: 160px;
    max-height: 160px;
    overflow-y: auto;
    overflow-x: auto;
    background: #202020 !important;
    border: none;
    border-right: 1px solid #272727; 
    color: white !important;
  }

  #test-input, #output {
    resize: none;
    padding: 6px;
  }

  .panel-body {
    padding: 0;
    margin: 0;
    border-radius: 0;
    height: 160px;
  }

  .panel-heading, .panel-input, .panel-output {
    width: calc(50vw - 7px);
    border-radius: 0;
    margin: 0;
  }

  .panel-heading {
    height: 40px !important;
    padding: 8px 15px;
    background: #272727;
    color: #fff;
    border-color: #272727;
  }

  .panel-input, .panel-output {
    position: absolute;
    bottom: 0;
    display: inline-block;
    height: 200px !important;
    max-height: 200px;
    border-color: #202020;
  }

  .panel-output {
    right: 14px;
  }

  @media (max-width: 767px) {
    .panel-heading, .panel, #output, #test-input {
      width: 100vw;
    }
  }
</style>
