# Google Summer of Code 2024, RocketChat

<div align="center">
    <a href="https://summerofcode.withgoogle.com/programs/2024/projects/eVxOuKT2"><img src="https://github.com/user-attachments/assets/9705b330-c4f9-4061-8c71-114cfb5153bb" width="720" alt="google-summer-of-code"></a>
</div>

## 📘 Introduction

During my GSoC period, I worked on EmbeddedChat, a lightweight chat widget that uses the RocketChat engine's REST and real-time APIs to deliver comprehensive chat features, customizable options, and attractive theming capabilities.

## ⭐ Project Abstract

The goal of this project was to develop a ready-to-use chat solution that could be integrated into any website, web app, or mobile app. In EmbeddedChat 2024, my focus was on enhancing the UI by making components modular and providing pre-built themes. The project also sought to ensure security through HTTP-Only cookie-based authentication, using RC-app as a bridge. I also worked on improving configuration capabilities, enabling the instance to be configurable through RC-app, and developed a real-time layout editor with drag-and-drop features, among other enhancements.

## 🚢 Deliverables

- Redesign Embedded Chat for consistent CSS, logic separation, and monorepo component management.
- Upgrade theming system with prebuilt themes and enhanced customization.
- Boost security with HTTP-Only cookie authentication in Embedded Chat via RC-app.
- Enable admins to easily adjust all Embedded Chat settings in Rocket.Chat Workspace.
- Offer a drag-and-drop editor for admin UI configuration without coding.
- Enhance UI-Kit integration.
- Fix bugs and improve documentation.

## 📹 Showcase

Explore a demonstration of the latest features and improvements. See firsthand how the updates enhance functionality and user experience.

### Sneak Peek

Here's a brief preview of EmbeddedChat integrated into a website, designed to demonstrate the functionality of RC apps without the need for local setup.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1f5da63d-b82e-497d-bade-cf88716297e8" width="720" alt="EC Integration">
</p>

### Code Refactor: Separation of Concerns

Key updates to the EmbeddedChat repository include:

1. **Separation of Components from Views**: Standalone components have been moved to a `ui-element` monorepo with its own Storybook.

2. **CSS Styles Separation**: CSS styles are now in a `component.styles.js` file, providing a clear separation from core logic.

3. **Markup and UI-Kit Separation**: Markups and the UI Kit are organized into a separate library (monorepo).

<p align="center">
  <img src="https://github.com/user-attachments/assets/b983d6c9-8190-4d5e-8a40-52588b07e7c3" width="720" alt="CSS styles in component.styles.js">
  <br>
  CSS styles are now in `component.styles.js`
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/77663956-2c74-4e54-a337-181abff094eb" width="720" alt="Separation into monorepo">
  <br>
  Separation into monorepo for `ui-elements`, `markups`, and `ui-kit`
</p>

The video below illustrates the development, usage, and setup of the ui-elements monorepo, and it also shows that EmbeddedChat functions as expected following this separation:

[UI-Elements Storybook](https://github.com/RocketChat/EmbeddedChat/assets/78961432/a399defd-cae7-495a-9f88-11f4b518df00)

### UI Theming Upgrade: Prebuilt Themes and Style Variants

The theming system has been enhanced with several prebuilt themes, ensuring a consistent use of theme colors across the repository. This replaces the previously inconsistent and varied color schemes.

Once the Storybook is running, you can explore and experiment with various designs within the `Design Variants` folder, including `RCVariant`, `Bubble Variant`, and `Modern Variant`. These options enable you to either use the prebuilt themes or draw inspiration to create your own. Below are images and videos demonstrating the different variants; note that the videos also highlight fixes introduced with these PRs:

[RC Variant](https://github.com/RocketChat/EmbeddedChat/assets/78961432/d9fea331-fa32-44df-8322-36c9fb2baa6c)

[Bubble Variant](https://github.com/RocketChat/EmbeddedChat/assets/78961432/06d61e66-8f17-423b-a339-1728323661b3)

<p align="center">
  <img src="https://github.com/RocketChat/EmbeddedChat/assets/78961432/826cf806-1d9c-4626-a3c2-4f00d8557389" width="720" alt="Automatically generated colors in usernames in dark mode + popup instead of sidebar">
  <br>
  Automatically generated colors in usernames in dark mode + popup instead of sidebar
</p>

<p align="center">
  <img src="https://github.com/RocketChat/EmbeddedChat/assets/78961432/b7efade3-b041-4311-a8a7-3e642b6f0de1" width="720" alt="Automatically generated colors in usernames in light mode + popup instead of sidebar">
  <br>
  Automatically generated colors in usernames in light mode + popup instead of sidebar
</p>

The theming system follows a convention similar to the ShadCN theming system. Users can generate themes from the ShadCN website or other sites that follow the same convention, then use the `packages/react/tools/theme-generator.js` to convert the theme into a supported format and apply it via the theme prop.

A demonstration video is available here:

[Theme Converter](https://github.com/user-attachments/assets/9078260f-1933-4be6-b019-61e9ac54be7d)

For further details on theming, you can visit the [documentation](https://rocketchat.github.io/EmbeddedChat/docs/docs/Usage/theming) or check out the [technical guide](https://rocketchat.github.io/EmbeddedChat/docs/docs/Development/theming_technical) for insights on how theming is implemented in the repository.

### Enhanced Authentication with HTTP-Only Cookies

EmbeddedChat authentication security has been enhanced through the use of HTTP-Only cookies for re-authentication. This approach adds an extra layer of protection by preventing access via inline JavaScript, thereby reducing the risk of potential attacks. To use this storage method, the EmbeddedChat RC app must be installed on the RC server, which acts as a bridge for saving and retrieving tokens. Once installed, you can test the feature using the Storybook `SecureAuth` option or by setting the `secure: true` prop during EmbeddedChat setup.

A video demonstration is available here:

[Http-Only-Cookie Auth](https://github.com/RocketChat/EmbeddedChat/assets/78961432/24fdf4bf-34b5-4e66-b045-802d6fc428dd)

For more information on authentication, refer to the [authentication guide](https://rocketchat.github.io/EmbeddedChat/docs/docs/Usage/authentication).

### UI-Kit Improvement

I enhanced the UI-Kit integration within EmbeddedChat by migrating it to a monorepo as a separate library. Key improvements include:

- **Modularized Structure**: Reorganized the UI-Kit folder structure for improved modularity.
- **Action Processing**: Added state and view update logic, along with parsing methods.
- **Contextual Bar Support**: Implemented support for the contextual bar.
- **Component Enhancements**: Added support for static select and multi-select elements with custom components and new component stories.

Testing was conducted across three distinct RC apps, with video demonstrations provided:

1. **Reminder RC App**:

[Reminder App UI-Kit Test](https://github.com/RocketChat/EmbeddedChat/assets/78961432/eeb17fd6-68f2-4113-8ef1-dc0faf32ca05)

2. **Notion RC App**:

[Notion App UI-Kit Test](https://github.com/RocketChat/EmbeddedChat/assets/78961432/71d9baa1-a54d-4077-9fbd-f7e005742f77)

3. **News Aggregation App** (tested multi-select functionality):

[News App UI-Kit Test](https://github.com/RocketChat/EmbeddedChat/assets/78961432/d3f611b0-3205-483f-b00a-9800893b98fb)

### EmbeddedChat Remote Configurability

I have added support for remote configuration of EmbeddedChat props, including themes, via the EmbeddedChat RC App. The app can also validate CSS dimensions provided in the settings. To try this feature, set up the RC app in your Rocket.Chat workspace and use the Storybook option `WithRemoteOpt` or pass the `remoteOpt: true` prop during EmbeddedChat setup.

The following videos demonstrate its usage:

[Remotely Configure EC](https://github.com/RocketChat/EmbeddedChat/assets/78961432/8f2e5027-2a8d-4723-8c2b-33ae7cbf9336)

[CSS Validation Test](https://github.com/RocketChat/EmbeddedChat/assets/78961432/2eaa4e50-ad38-4ac8-8cc7-d8eebd875f26)

To set up the EmbeddedChat RC App, follow this guide: [EmbeddedChat RC App Setup](https://rocketchat.github.io/EmbeddedChat/docs/docs/Usage/ec_rc_setup).

### Layout Editor

I also worked on a new sub-project called `layout-editor` during GSoC to enhance EmbeddedChat customizability. This tool enables users to customize the EmbeddedChat layout in real-time with drag-and-drop features, color configuration, and more. Once satisfied with their design, users can click the `Generate Theme` button to create a theme object, which can be applied by passing it into the theme prop during EmbeddedChat setup or by configuring it remotely if EmbeddedChat RC App is properly set up.

A video demonstration showcases the features:

[Layout Editor Demo](https://github.com/user-attachments/assets/3f846616-bf33-49ca-95c7-3a6e98685476)

To learn more about the layout editor, visit the guide: [Layout Editor Guide](https://rocketchat.github.io/EmbeddedChat/docs/docs/Usage/layout_editor).

## 🚀 Contributions

### GSoC Contributions to EmbeddedChat

| PR ID | Title                                                                                                                      |
| ----- | -------------------------------------------------------------------------------------------------------------------------- |
| 576   | Refactor, Restructure, and Fix Bugs ([#576](https://github.com/RocketChat/EmbeddedChat/pull/576))                          |
| 579   | UI Theming Upgrade and RC-like Redesign ([#579](https://github.com/RocketChat/EmbeddedChat/pull/579))                      |
| 581   | Add Curved Bubble Variant Styles ([#581](https://github.com/RocketChat/EmbeddedChat/pull/581))                             |
| 584   | More Customization: Popup/Sidebar and Username Color Options ([#584](https://github.com/RocketChat/EmbeddedChat/pull/584)) |
| 589   | Fix ChatInput Bugs, Improve Experience ([#589](https://github.com/RocketChat/EmbeddedChat/pull/589))                       |
| 590   | Enhance Security with HTTP-Only Cookies ([#590](https://github.com/RocketChat/EmbeddedChat/pull/590))                      |
| 591   | Remove Unused Files ([#591](https://github.com/RocketChat/EmbeddedChat/pull/591))                                          |
| 593   | UI-Kit Integration and Action Processing ([#593](https://github.com/RocketChat/EmbeddedChat/pull/593))                     |
| 594   | Auto Login Improvements and Loading Screens ([#594](https://github.com/RocketChat/EmbeddedChat/pull/594))                  |
| 599   | Remote EmbeddedChat Settings Configuration ([#599](https://github.com/RocketChat/EmbeddedChat/pull/599))                   |
| 601   | Add CSS Dimension Validation ([#601](https://github.com/RocketChat/EmbeddedChat/pull/601))                                 |
| 602   | Documentation Improvements ([#602](https://github.com/RocketChat/EmbeddedChat/pull/602))                                   |
| 604   | Separate Component Monorepo (UI-Elements) ([#604](https://github.com/RocketChat/EmbeddedChat/pull/604))                    |
| 606   | Reduce Package Size of Component Monorepo ([#606](https://github.com/RocketChat/EmbeddedChat/pull/606))                    |
| 607   | Add Real-Time Layout Editor with Drag-and-Drop ([#607](https://github.com/RocketChat/EmbeddedChat/pull/607))               |

[See all PRs for EmbeddedChat](https://github.com/RocketChat/EmbeddedChat/pulls?q=is%3Apr+author%3ASpiral-Memory)

In addition to working on EmbeddedChat, I've made contributions to several other RocketChat projects. Check out my pull requests for [Apps.Notion](https://github.com/RocketChat/Apps.Notion/pulls?q=+is%3Apr+author%3ASpiral-Memory), [Rocket.Chat](https://github.com/RocketChat/Rocket.Chat/pulls?q=+is%3Apr+author%3ASpiral-Memory), and [Fuselage](https://github.com/RocketChat/fuselage/pulls?q=+is%3Apr+author%3ASpiral-Memory).

## 🎓 A Special Thanks to My Mentor

Thank you so much to Sidharth Mohanty for being an amazing mentor during GSoC. He’s been incredibly receptive to ideas, always available to help, and provides great guidance during our meetups. His encouragement to explore new areas has made this experience really rewarding. I’ve learned a lot from him and truly appreciate all his support.

You can connect with him on [GitHub](https://github.com/sidmohanty11), [LinkedIn](https://www.linkedin.com/in/sidmohanty11/), and [Twitter](https://twitter.com/sidmohanty11).

## 🔗 Links

Download and read my EmbeddedChat project proposal, which led to my GSoC acceptance, [here](https://github.com/Spiral-Memory/GSoC-Proposal/blob/main/Embedded%20Chat%202024%20GSoC%20Proposal%20%5BWinning%5D.pdf).

## ❤️ Support

Enjoyed what you learned today? Show your appreciation by starring this repo. ⭐

## 💬 Let's Connect

Interested in chatting about GSoC, Rocket.Chat, or open-source adventures? I'm all ears!

| **Role**           | **Zishan Ahmad – GSoC Participant**                                                      |
| :----------------- | :--------------------------------------------------------------------------------------- |
| **Affiliation**    | [Rocket.Chat](https://rocket.chat/)                                                      |
| **Project**        | [EmbeddedChat 2024](https://summerofcode.withgoogle.com/programs/2024/projects/eVxOuKT2) |
| **GitHub**         | [@Spiral-Memory](https://github.com/Spiral-Memory)                                       |
| **LinkedIn**       | [@zishanahmad72](https://www.linkedin.com/in/zishanahmad72/)                             |
| **Creative Space** | [spiral-memory.netlify.app](https://spiral-memory.netlify.app/)                          |
| **Email**          | [zishan.barun@gmail.com](mailto:zishan.barun@gmail.com)                                  |
| **Rocket.Chat**    | [zishan.ahmad](https://open.rocket.chat/direct/zishan.ahmad)                             |

## 📌 Closing Notes

This repository contains the final report and serves as a guide for future contributors to the EmbeddedChat project, which was developed and improved during Google Summer of Code (GSoC) 2024. The final report details the solutions implemented during the project, while the guide provides insights and instructions for new contributors to effectively engage with and build upon the project's foundation.
