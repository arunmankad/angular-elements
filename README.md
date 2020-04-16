# AngularElements

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 8.3.5.

Please check out the project, use   `npm install` install all the dependencies.

## Web Component!

Other changes from a standard angular cli project to watch out for.

In app.module.ts
```js
import { BrowserModule } from '@angular/platform-browser';
import { NgModule, Injector } from '@angular/core';
import { createCustomElement } from '@angular/elements';

import { AppComponent } from './app.component';
import { ProgressbarComponent } from './progressbar/progressbar.component';

@NgModule({
  declarations: [
    AppComponent,
    ProgressbarComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  // bootstrap: [AppComponent],
  entryComponents: [AppComponent, ProgressbarComponent]
})
export class AppModule {
  constructor(public injector: Injector) {}

  ngDoBootstrap() {
    const PorgressbarElement = createCustomElement(ProgressbarComponent, {
      injector: this.injector
    });

    customElements.define('progressbar-element', PorgressbarElement);
  }
}

```
Other items to note `ng add @angular\elements` 
2 dependencies added into package.json are `document-register-element & @angular/elements`

build using the command `npx ng build --prod`

Start a http server like `http-server` from the dist folder the see the web components in action!