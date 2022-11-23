"use strict";(globalThis.webpackChunk=globalThis.webpackChunk||[]).push([["app_assets_modules_github_filter-input_ts"],{72122(a,b,c){c.d(b,{a:()=>BaseFilterElement});var d=c(36162),e=c(4738),f=c(59753),g=c(47448),h=c(54650),i=c(76006),j=c(41311),k=function(a,b,c,d){var e,f=arguments.length,g=f<3?b:null===d?d=Object.getOwnPropertyDescriptor(b,c):d;if("object"==typeof Reflect&&"function"==typeof Reflect.decorate)g=Reflect.decorate(a,b,c,d);else for(var h=a.length-1;h>=0;h--)(e=a[h])&&(g=(f<3?e(g):f>3?e(b,c,g):e(b,c))||g);return f>3&&g&&Object.defineProperty(b,c,g),g};let l=new Map;class BaseFilterElement extends HTMLElement{async cachedJSON(a){let b=await fetch(a,{headers:{"X-Requested-With":"XMLHttpRequest",Accept:"application/json"}});if(!b.ok){let c=Error(),d=b.statusText?` ${b.statusText}`:"";throw c.message=`HTTP ${b.status}${d}`,c}return b.json()}fetchQualifierSuggestions(){let a="data-suggestable-qualifiers",b=this.searchInput.getAttribute(a);if(null===b)throw Error(`
        ${a} is missing from ${this.searchInput.getAttribute("data-target")}.
        Either add it or override fetchQualifierSuggestions.
      `);return JSON.parse(b)}negatableQualifiers(){return JSON.parse(this.searchInput.getAttribute("data-negatable-qualifiers")||"[]")}removeNegationFromQualifierIfSupported(a){if(!a.startsWith("-"))return a;let[b,...c]=a.split(":"),d=b.substring(1);return this.negatableQualifiers().includes(d)&&(b=d),a.includes(":")&&(b+=":"),c?.length>0?`${b}${c.join(":")}`:b}fetchSuggestionsForQualifier(a){a=this.removeNegationFromQualifierIfSupported(a);let b=`data-suggestable-${a}`,c=`data-suggestable-${a}-path`;if(this.searchInput.hasAttribute(b))return JSON.parse(this.searchInput.getAttribute(b)||"[]");if(!this.searchInput.hasAttribute(c))return Promise.resolve([]);{let d=this.searchInput.getAttribute(c);if(!d)throw Error(`${c} not set`);return this.cachedJSON(d)}}hideFilterSuggestions(){(0,e.jK)(this.searchForm),this.autocompleteDropdown.hidden=!0,this.searchInput.setAttribute("aria-expanded","false"),this.searchInput.removeAttribute("aria-activedescendant")}updateFilterSuggestionResults(){let a=this.searchInput.value,b=a.slice(0,this.searchInput.selectionEnd),c=(b.match(/(:"[^"]+"?|\S)+$/)||[""])[0].replace(/"/g,"");this.autocompleteDropdown.hidden=!1,this.searchInput.setAttribute("aria-expanded","true");let d,f;c.includes(":")?[d,...f]=c.split(":"):d=c,null!=f?this.renderValueSuggestions(d,f.join(":")):this.renderQualifierSuggestions(d),a.trim().length>0&&(!this.invalidSearchTerms()||this.showSubmissionOptionIfInvalidSearchTerms)&&!this.searchMatchesDefault()?(this.clearButton&&(this.clearButton.hidden=!1),(0,e.T_)(this.searchForm)):(this.clearButton&&(this.clearButton.hidden=!0),(0,e.QZ)(this.searchForm))}handleSelectedSuggestionResultEvent(a){let b=a.target;if(b.classList.contains("js-filter-input-support-url"))return;if(b.hasAttribute("data-search")){(0,h.Bt)(this.searchForm);return}let c=b.getAttribute("data-value")||"";":"!==c[c.length-1]&&(c+=" ");let d=this.searchInput.value.slice(0,this.searchInput.selectionEnd),e=d.match(/(\S+)$/)?.pop()||"",g=this.searchInput.value.slice(this.searchInput.selectionEnd),i=" "!==g[0]?" ":"";if(e&&(e.startsWith("-")&&!c.startsWith("-")&&(c=`-${c}`),e.includes(","))){let j=e.split(",");j.pop();let k=c.split(":").slice(1).join(":");j.push(k||""),c=j.join(",")}let l=d.replace(/\S+$/,"");this.searchInput.value=l+c+i+g,a.preventDefault(),this.searchInput.focus();let m=l.length+c.length;this.searchInput.setSelectionRange(m,m),(0,f.f)(this.searchInput,"input")}handleFormKeydownEvent(a){"Enter"===a.detail.hotkey&& !(this.autocompleteResults.querySelector(".js-filter-loading")||this.autocompleteResults.querySelector(".js-navigation-item.navigation-focus"))&&(0,h.Bt)(this.searchForm)}clear(){this.searchInput.value=this.getDefaultSearch(),0===this.getInitialValue().trim().length?this.updateFilterSuggestionResults():(0,h.Bt)(this.searchForm)}renderQualifierSuggestions(a){this.showAllQualifiersIfNoneMatch?this.renderMatchingOrAllQualifierSuggestions(a):this.renderMatchingQualifierSuggestions(a)}handleSuggestionNavigation(a){null!=a.target&&this.searchInput.setAttribute("aria-activedescendant",a.target.id)}renderMatchingOrAllQualifierSuggestions(a){let b=this.fetchQualifierSuggestions(),c=this.filterSuggestionsList(b,a,{fuzzy:this.fuzzyMatchQualifiers}).then(a=>0===a.length?b:a);this.renderSuggestionDropdown(c)}renderMatchingQualifierSuggestions(a){let b=this.filterSuggestionsList(this.fetchQualifierSuggestions(),a,{fuzzy:this.fuzzyMatchQualifiers});this.renderSuggestionDropdown(b)}renderValueSuggestions(a,b){let c=this.fetchMatchingSuggestions(a,b);this.renderSuggestionDropdown(c)}async fetchMatchingSuggestions(a,b){let c=this.fetchSuggestionsForQualifier(a),d=b.split(",").pop()||"",e=await this.filterSuggestionsList(c,d,{fuzzy:this.fuzzyMatchValues});return e.map(b=>({value:`${a}:${b.value}`,description:b.description}))}async filterSuggestionsList(a,b,{fuzzy:c}={fuzzy:!0}){let d=await a,e=b.trim().toLowerCase();return e&&0!==e.length?(e.startsWith("-")&&(e=e.slice(1)),d.filter(a=>c?a.value.toLowerCase().includes(e):a.value.toLowerCase().startsWith(e))):d}renderSuggestionDropdown(a){(0,d.sY)(d.dy`
        <div role="listbox" aria-label="${this.suggestionsTitle}">
          ${this.renderSearchWarningIfRequired()}
          ${this.shouldRenderSubmissionOption()?this.renderSearchSuggestion():""}
          ${(0,j.C)(this.renderSuggestionList(a),this.renderLoadingItem())}
        </div>
      `,this.autocompleteResults),this.postDropdownRender()}renderSearchWarningIfRequired(){let a=this.invalidSearchTerms();if(!a||0===a.length)return"";let b=d.dy``,c=this.getFilterSupportURL();return c&&(b=d.dy`<a
        class="js-navigation-item js-navigation-open js-filter-input-support-url px-1"
        href="${c}"
        target="_blank"
      >
        Learn more about filters.
      </a>`),d.dy`
      <div class="color-bg-attention color-fg-muted ml-n2 mr-n2 mt-n1 py-1 px-2 js-search-warning-container">
        Sorry, we don't support the <span class="text-bold">${a}</span> filter yet. ${b}
      </div>
    `}getFilterSupportURL(){return this.searchInput.getAttribute("data-filter-support-url")}postDropdownRender(){}renderSearchSuggestion(){let a=this.searchInput.value.trim();return 0===a.length||/:\s|:$/g.test(a)&&!/(?:\w+:){2,}/g.test(a)?d.dy``:d.dy`
      <div
        id="${this.getComponentTagName()}-search-submit-option"
        class="border-bottom-0 rounded-2 py-1 px-2 mx-0 mb-1 js-navigation-item"
        data-action="navigation:focus:${this.getComponentTagName()}#handleSuggestionNavigation"
        data-search="true"
        role="option"
      >
        <span class="text-bold">${a}</span> - submit
      </div>
    `}invalidSearchTerms(){let a=this.fetchQualifierSuggestions().map(a=>a.value),b=RegExp(/[^\s:]+:/),c=RegExp(/"(?:\\"|.)*?"/),d=RegExp(`${b.source}(?:${c.source}|[^\\s]*)`),e=RegExp(/[^\s]+/),f=RegExp(`${d.source}|${e.source}`,"g"),g=this.searchInput.value.match(f)||[],h=g.filter(b=>{b=this.removeNegationFromQualifierIfSupported(b);let c=b.indexOf(":");if(-1===c)return this.unqualifiedSearchTermsAlwaysValid?null:!a.some(a=>a.startsWith(b));{let d=b.substr(0,c+1);return!a.some(a=>a===d)}});return 0===h.length?null:h.join(" ")}searchMatchesDefault(){let a=this.searchInput.value.trim().split(" ").sort(),b=this.getDefaultSearch().trim().split(" ").sort();return a.length===b.length&&a.every((a,c)=>a===b[c])}getInitialValue(){return this.getDataAttributeOrThrow("data-initial-value")}getComponentTagName(){return this.tagName.toLowerCase()}getDefaultSearch(){return this.getDataAttributeOrThrow("data-default-value")}getDataAttributeOrThrow(a){let b=this.searchInput.getAttribute(a);if(null===b)throw Error(`${a} is missing from search input`);return b}renderSuggestionsTitle(){return d.dy`<p
      class="h6 width-full text-normal border-bottom color-bg-default color-fg-muted py-2 mb-2"
      aria-hidden="true"
    >
      ${this.suggestionsTitle}
    </p>`}async renderSuggestionList(a){let b=await a,c=b.map((a,b)=>d.dy`
          <div
            class="border-bottom-0 rounded-2 py-1 px-2 mx-0 mb-1 js-navigation-item"
            data-value="${a.value}"
            data-action="navigation:focus:${this.getComponentTagName()}#handleSuggestionNavigation"
            aria-label="${a.value} ${a.description}"
            id="${this.getComponentTagName()}-suggestion-${b}"
            role="option"
          >
            <span class="text-bold">${a.value}</span>${this.spaceBetweenValueAndDescription?" ":""}<span
              class="autocomplete-text-qualifier color-fg-muted"
              >&nbsp;${a.description}</span
            >
            ${a.isAlpha&&this.alphaTag} ${a.isBeta&&this.betaTag}
            ${a.isNew?this.newTag:""}
          </div>
        `);return c.length&&c.unshift(this.renderSuggestionsTitle()),c}renderLoadingItem(){return d.dy`
      ${this.renderSuggestionsTitle()}
      <span class="js-filter-loading">loading...</span>
    `}handleSearchBlur(){this.hideFilterSuggestions(),this.selectorOfElementToActivateOnBlur&&(0,e.QZ)(document.querySelector(this.selectorOfElementToActivateOnBlur))}inputKey(a){"Escape"===a.key&&this.handleSearchBlur()}shouldRenderSubmissionOption(){return this.showSubmissionOptionIfInvalidSearchTerms||!this.invalidSearchTerms()}static tagFn(a){return d.dy`<span class="lh-condensed px-1 rounded-2 border color-border-success">${a}</span>`}constructor(...a){super(...a),this.showAllQualifiersIfNoneMatch=!0,this.fuzzyMatchQualifiers=!1,this.fuzzyMatchValues=!0,this.showSubmissionOptionIfInvalidSearchTerms=!1,this.suggestionsTitle="Available filters",this.spaceBetweenValueAndDescription=!0,this.selectorOfElementToActivateOnBlur=null,this.unqualifiedSearchTermsAlwaysValid=!0,this.alphaTag=BaseFilterElement.tagFn("Alpha"),this.betaTag=BaseFilterElement.tagFn("Beta"),this.newTag=d.dy`<span class="Label ml-1 Label--accent color-bg-default float-right">New</span>`}}k([i.fA],BaseFilterElement.prototype,"autocompleteDropdown",void 0),k([i.fA],BaseFilterElement.prototype,"autocompleteResults",void 0),k([i.fA],BaseFilterElement.prototype,"clearButton",void 0),k([i.fA],BaseFilterElement.prototype,"searchForm",void 0),k([i.fA],BaseFilterElement.prototype,"searchInput",void 0),k([(0,g.Z)({cache:l})],BaseFilterElement.prototype,"cachedJSON",null)}}])
//# sourceMappingURL=app_assets_modules_github_filter-input_ts-fa570ac7cdf4.js.map