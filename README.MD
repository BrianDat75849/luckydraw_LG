# Lottery program

Annual meeting lottery program, 3D sphere lottery, support for configuration of prize information, import of lottery information by `Excel`, and export of lottery results by `Excel`

If this program is helpful to you 😎😎😎, I hope to give it a ⭐**star**⭐. 😘😘😘😍🥰🎉🎈🎃

> Try it now: [https://moshang-xc.github.io/lottery/](https://moshang-xc.github.io/lottery/)

## technology

Technology: Node + Express + Three.js

The background is implemented through `Express`

The front-end lottery interface implements 3D lottery balls through `Three.js`, citing the official 3D example of `Three.js`

## Function description:

1. The lottery results can be saved and downloaded to excel in real time🎉
2. Those who have been drawn will not participate in the draw, and those who have been drawn can re-draw if they are not on the scene🎁
3. Refresh or turn off the server, the current drawn data will be saved, and the data will not be reset. Only by clicking the reset button on the interface can the lottery data be reset🧧
4. The number of prizes drawn each time is configurable🎈
5. After drawing all prizes, you can continue to draw special prizes (for example: draw red envelopes now, additional prizes, etc.), and at this time, one will be drawn at a time by default 🧨

## preview

![lottery.gif](https://raw.githubusercontent.com/moshang-xc/blog/master/share/lottery.gif)

![index.jpg](https://raw.githubusercontent.com/moshang-xc/blog/master/share/index.jpg)

![start.jpg](https://raw.githubusercontent.com/moshang-xc/blog/master/share/start.jpg)

![end.jpg](https://raw.githubusercontent.com/moshang-xc/blog/master/share/end.jpg)

## Install

```
git clone https://github.com/moshang-xc/lottery.git

cd lottery

# Server plugin installation
cd server
npm install

# Front-end plugin installation
cd ../product
npm install

# Bale
npm run build

# run
npm run serve

# Development and debugging
npm run dev

```

## Directory Structure

```
lottery
├── product
│ ├── src
│ │ ├── lottery
│ │ │ └── index.js
│ │ ├── lib
│ │ ├── img
│ │ ├── css
│ │ └── data
│ ├── package.json
│ └── webpack.config.js
├── server
│ ├── config.js
│ ├── server.js
│ └── package.js
```

> 1. product is the front-end page directory
> 2. package.josn web project configuration file
> 3. webpack.config.js packaging configuration file
> 4. server is the server directory
> 5. config is the configuration file of prize information

## configuration information

### Lottery user information configuration

The lottery user information is in the **`server/data/user.xlsx`** file, which is filled according to the file format, and the file name and column header cannot be modified

### Prize information configuration

The prize configuration information is filled in the **server/config.js** file, and the file name cannot be modified.

**The configuration description of the prizes is as follows:**

| Parameter | Value Type | Description |
| ----- | ------ | ------------------------------------ ------------------------ |
| type | Number | Prize type, unique identifier, 0 is the placeholder for the default special prize, other prizes cannot be used |
| count | Number | Number of prizes |
| text | String | Award name |
| title | String | Prize description |
| img | String | The image address of the prize, the image is under the **img** directory |

```js
// Prize information, the first item is reserved and cannot be modified, other items can be modified as needed
let prizes = [{
        type: 0,
        count: 1000,
        title: "",
        text: "Special Award"
    },
    {
        type: 1,
        count: 2,
        text: "Grand Prize",
        title: "Mysterious Gift",
        img: "../img/secrit.jpg"
    },
    {
        type: 2,
        count: 5,
        text: "First Prize",
        title: "Mac Pro",
        img: "../img/mbp.jpg"
    }
    ...
];
```

### Configuration of the number of prizes drawn each time

**EACH_COUNT** is used to configure the number of draws each time, which corresponds to the prizes one by one. For example, the configuration of the number of draws corresponding to the above prize configuration is as follows:

```js
const EACH_COUNT = [1, 1, 5];
```

The above configuration means that the order of the number of prizes to be drawn at one time is: one special prize is drawn each time, one special prize is drawn each time, and five first prizes are drawn each time

### Enterprise Identity Configuration

This logo is used to display on the draw card.

```js
const COMPANY = "MoShang";
```
## License
MIT