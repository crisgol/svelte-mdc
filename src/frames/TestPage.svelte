<script>
	import {
		Button, Fab, Card, Checkbox,
		Dialog, DialogButton, LinearProgress,
		Icon, IconToggle,
		Body, Subheading, Title, Display, Headline,
    LayoutGrid,
    LayoutGridCell,
		LayoutGridInner,
		Menu, MenuItem,
		Tab, TabBar, TabScroller
  } from '../components';
  import { TextField } from '../components';

  export let name = '';
  export let text = '';
  export let outlined = true;
  export let disabled = false;

  let label = 'label';
  let activeIndex = 0;

	function updatePanel(e) {    
    activeIndex = e.detail.activeTabIndex;
  }
</script>

TextField


<!--  -->
<div class="component-container">
  <div class="component-demo component-demo--open">
    <div class="component-demo__content">
      <div class="component-demo__app-bar">
        <div class="component-demo__tab-section">
          <TabBar on:change={updatePanel} >
            <TabScroller>
              <Tab href="#filled" active className="component-demo__tab" >
                Filled
              </Tab>
              <Tab href="#outlined" className="component-demo__tab" >
                Outlined
              </Tab>
            </TabScroller>
          </TabBar>
        </div>
      </div>
      <div class="component-demo__stage-content">
        <div id="filled" class="stage-transition-container-variant" class:stage-transition-container-variant--show={activeIndex == 0} >
          <div class="inline-text-field-container">
            <TextField id="TextField1" bind:value={text} {disabled} {label}/>
          </div> 
        </div>
        <div id="outlined" class="stage-transition-container-variant" class:stage-transition-container-variant--show={activeIndex == 1} >
          <div class="inline-text-field-container">
            <TextField id="TextField2" bind:value={text} outlined {disabled} {label}/>
          </div>
        </div>
      </div>
      <div class="component-demo__config-panel">
        <div class="component-demo__panel-header"> 
          <div class="component-demo__panel-header-label">
            IconButton
          </div>      
        </div>
        <div class="text-field-options">
          outlined
          <Checkbox bind:checked={outlined} />
          disabled
          <Checkbox bind:checked={disabled} />
        </div>
      </div>     
    </div>
  </div>
</div>

<style>

/* .component-demo__tab-section .mdc-tab-bar{width:auto}
.component-demo__tab{padding-right:12px;padding-left:12px}
.component-demo__tab .mdc-tab__text-label{color:rgba(0,0,0,.6)}
.component-demo__tab.mdc-tab--active .mdc-tab__text-label{color:rgba(0,0,0,.87)}
.component-demo__tab .mdc-tab-indicator__content--underline{border-color:#424242}
.component-demo__tab .mdc-tab__ripple::before,.component-demo__tab .mdc-tab__ripple::after{background-color:#616161}
.component-demo__tab .mdc-tab__ripple:hover::before{opacity:.04}
.component-demo__tab .mdc-tab__ripple:not(.mdc-ripple-upgraded):focus::before,.component-demo__tab .mdc-tab__ripple.mdc-ripple-upgraded--background-focused::before{transition-duration:75ms;opacity:.12}
.component-demo__tab .mdc-tab__ripple:not(.mdc-ripple-upgraded)::after{transition:opacity 150ms linear}
.component-demo__tab .mdc-tab__ripple:not(.mdc-ripple-upgraded):active::after{transition-duration:75ms;opacity:.12}
.component-demo__tab .mdc-tab__ripple.mdc-ripple-upgraded{--mdc-ripple-fg-opacity: 0.12}
.component-demo__tab .mdc-tab-indicator{bottom:1px;height:auto}
.component-demo__config-button,.component-demo__panel-header-close{border-radius:0;height:100%;color:#000;opacity:.54;transition:visibility 0s linear 225ms}
.component-demo__config-button:hover,.component-demo__panel-header-close:hover{opacity:.87} */
/* .stage-transition-container-variant{position:absolute;padding:40px;bottom:0;left:0;right:0;top:0;align-items:center;display:flex;justify-content:center;opacity:0;transition-duration:250ms;transition-property:opacity,visibility;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);visibility:hidden;z-index:0}
.stage-transition-container-variant--show{opacity:1;visibility:visible} */

  .component-container {
    border: 1px solid rgba(0,0,0,.12);
    width: 100%;
    height: 400px;
  }
  .component-demo {
    height: 100%;
    display: flex;
    flex-direction: row;
  }
  .component-demo .component-demo__content {
    flex-direction: column;
    display: flex;
    height: 100%;
    width: 100%;
    transition: width;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 250ms;
  }
  
  .component-demo .component-demo__config-panel{background-color:#fff;border-left:1px solid rgba(0,0,0,.1);position:fixed;right:-200px;z-index:10;height:100%;width:200px;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:250ms;transition-property:right}
  .component-demo .component-demo__panel-header{height:48px;padding-left:16px;padding-right:4px;border-bottom:1px solid #eee;display:flex;justify-content:space-between}
  .component-demo .component-demo__panel-header-label{font-family:Roboto,sans-serif;-moz-osx-font-smoothing:grayscale;-webkit-font-smoothing:antialiased;font-size:.875rem;line-height:1.375rem;font-weight:500;letter-spacing:.0071428571em;text-decoration:inherit;text-transform:inherit;display:flex;align-items:center;flex:1 1 auto;line-height:1.25rem;font-weight:400;opacity:.87}

  .component-demo--open .component-demo__content{width:calc(100% - 200px)}
  .component-demo--open .component-demo__config-panel{right:0}
  .component-demo--open .component-demo__config-button{visibility:hidden;transition-delay:0ms}

  /* .component-demo__stage-content{background:#fff;flex:1 1 auto;min-height:250px;position:relative}
  .component-demo__app-bar{background-color:#fff;flex-shrink:0;height:48px;padding-left:16px;padding-right:4px;border-bottom:1px solid #eee;display:flex}
  .component-demo__tab-section{display:flex;flex:1 1 auto;justify-content:flex-start} */

  .component-demo__app-bar {
    background-color: #fff;
    flex-shrink: 0;
    height: 48px;
    padding-left: 16px;
    padding-right: 4px;
    border-bottom: 1px solid #eee;
    display: flex;
  }
  .component-demo__tab-section {
    display: flex;
    /* flex: 1 1 auto;  */
    justify-content: flex-start;
  }
  .component-demo__tab {
    padding-right: 12px;
    padding-left: 12px;
  }
  .component-demo__stage-content {
    background: #fff;
    flex: 1 1 auto;
    min-height: 250px;
    position: relative;
  }
  .component-demo .component-demo__panel-header {
    height: 48px;
    padding-left: 16px;
    padding-right: 4px;
    border-bottom: 1px solid #eee;
    display: flex;
    justify-content: space-between;
  }
  .text-field-options {
    padding: 4px 4px 16px;
  }
  .stage-transition-container-variant {
    position: absolute;
    padding: 40px;
    bottom: 0;
    left: 0;
    right: 0;
    top: 0;
    align-items: center;
    display: flex;
    justify-content: center;
    opacity: 0;
    transition-duration: 250ms;
    transition-property: opacity,visibility;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    visibility: hidden;
    z-index: 0;
  }
  .stage-transition-container-variant--show {
    opacity: 1;
    visibility: visible;
  }
  .inline-text-field-container {
    display: flex;
    flex-direction: column;
  }
  .component-demo .component-demo__panel-header-label {
    font-family: Roboto,sans-serif;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    font-size: .875rem;
    line-height: 1.375rem;
    font-weight: 500;
    letter-spacing: .0071428571em;
    text-decoration: inherit;
    text-transform: inherit;
    display: flex;
    align-items: center;
    flex: 1 1 auto;
    line-height: 1.25rem;
    font-weight: 400;
    opacity: .87;
  }
</style>