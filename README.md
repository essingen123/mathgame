<!DOCTYPE html>
<html>

<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title> 1000 Decimals of Pi • MATH GAME v0.007a • 😀 Coded on a Mobile FastSpaghetti Prototype</title>
    <!-- 😀 Coded mostly on a Mobile, Fast Prototype . 
So intentionally not made with quality code, just to test out if it works -->
    <style>
        #answer {
            position: fixed;
            opacity: 0.9;
            left: 45%;
            outline: none;
            border: none;
            background-color: none;
            background: none;
        }

        i3 {
            text-shadow: 0 0 10px rgb(222, 204, 16), 0 0 20px rgb(198, 142, 0), 0 0 30px #ff8400, 0 0 40px #ff9900, 0 0 50px #e66b00, 0 0 60px #f4a600, 0 0 70px #ffeec8;
            text-align: center;
            /* background-color: #fb5; */
            background-color: #fb5;

            background-color: #ff4e00;
            background-image: linear-gradient(315deg, #ff4e00 0%, #ec9f05 74%);


            padding: 3px;
            color: #ffd8ba;
            margin: 1px auto 1px auto;
            font-style: italic;
            display: block;
            border: 8px solid #efefef99;
            font-size: 250%;
            width: 100%;
            padding: 8px;
            /* height:50%; */
            /*white-space: nowrap;*/
            /*transition: all 0.5s;*/
            /* transition: all 0.5s ease-in-out; */
        }

        i3::before {
            content: '';
        }

        i3::after {
            content: '';
        }

        .scoreoverlay {
            margin-top: 1900px;
            display: none;
            opacity: 0.6;
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: 100;
            left: 0;
            top: 0;
            background: radial-gradient(circle at 50% 30%, #f22f2299, #f29 40%);
            font-size: 120%;
            color: #ffffff;
            font-weight: bolder;
            font-style: italic;
            padding-top: 20px;
            /* transition: all 2s ease-in-out; */
            border-radius: 30px;
            animation-name: fadein;
            animation-duration: .4s;
        }

        @keyframes fadein {
            0% {
                opacity: 1;
              
            }

            100% {
                opacity: 1;
                top: 0;
                /* left: var(--fbpowoutho); */
            }
        }

        .show {
            display: block;
            margin-top: 0;
            border-radius: 0;
            opacity: 1;
            transition: all 2s ease-in-out;
            transition-timing-function: cubic-bezier(.12, 1.38, .44, .98);
        }

        :root {
            /*	--delay: 5;
	--elapsed: 20s;
	*/
            --fbpowro: -3deg;
            --fbpowoutho: -3deg;
        }

        .fb {
            left: 0;
            right: 0;
            bottom: 100%;
            position: fixed;
            opacity: 0;
            width: 120px;
            height: 110px;
            background-color: #a7e3b3;
            border-radius: 50%;
            text-align: center;
            margin: 4% auto;
            border: solid 9px #bfb;
            font-size: 170%;
            z-index: 200;
            padding-top: 30px;
            filter: drop-shadow(2px 2px 13px #ffeefa);
            color: #a0c9a5;
        }

        .fbpow {
            animation-duration: 0.8s;
            animation-name: fbpow;
            /*   animation-iteration-count: 1;
            animation-direction: forward;*/
            /*
animation-timing-function: cubic-bezier(0.3, -0.1, 0.2, 1.4);
*/
            z-index: 200;
        }

        @keyframes fbpow {
            0% {
                bottom: 22%;
                transform: rotateZ(var(--fbpowro));
                margin: 5% auto;
            }

            

            50% {
                opacity: 0.8;
                bottom: 50%;
                border: solid 1px #bfb;
                transform: rotateZ(0deg);

            }

            100% {
                opacity: 0;
                bottom: 87%;
                width: 50%;
                transform: rotateZ(4deg);

                /* left: var(--fbpowoutho); */
            }
        }

        .score {
            position: absolute;
            top: 0;
            left: 0;
            padding: 5px;
        }

        .scorebar {
            display: block;
            /* background-color: #fafafa77; */
            margin: 0;
            padding: 0;
            width: 100%;
            height: 30px;
            position: absolute;
            top: 0;
        }

        .hiscore {
            position: absolute;
            top: 0;
            right: 0;
            padding-top: 5px;
        }

        #scoring {
            display: block;
            background-color: #ccc;
        }

        .wrapper {
            background-color: #fefefe11;
            margin: 12px 0;
            padding: 0;
        }

        spansmall {
            font-size: 0.7rem;
            line-height: 2px;
            padding: 0;
            margin: 0;
        }

        #timer {
            width: 2px;
            line-height: 0px;
            border: solid 2px rgb(223, 247, 222, 0.3);
            margin-top: 2px;
            padding: 0;
            text-align: center;
            border-radius: 4px;
            display: inline-block;
            height: 27px;
            background: #77ff88;
            transition: all 0.2s ease-in-out;
            transition-timing-function: cubic-bezier(0.175, 0.885, 0.32, 1.275);
            filter: drop-shadow(2px 0 15px #2bff0066);
        }

        .progressbarboss {
            width: 100%;
            margin: -3px auto;
            padding: 0;
            line-height: 0px;
            /*border: solid 1px #eee;
  z-index:2;*/
        }

        .progressbar {
            width: 100%;
            margin: -3px auto;
            padding: 0;
            line-height: 0px;
            /*border: solid 1px #eee;
  z-index:2;*/
        }

        .progressbar .inner {
            line-height: 0;
            margin: 1px;
            padding: 0;
            text-align: center;
            display: inline-block;
            height: 18px;
            animation: progressbar-countdown;
            animation-duration: 20s;
            /*var(--elapsed);*/
            /* We stop in the end */
            animation-iteration-count: 1;
            /* Stay on pause when the animation is finished finished */
            animation-fill-mode: forwards;
            /* We start paused, we start the animation using javascript */
            animation-play-state: paused;
            /* We want a linear animation, ease-out is standard */
            animation-timing-function: linear;
            /*animation-delay: var(--delay);*/
        }

        @keyframes progressbar-countdown {
            0% {
                width: 100%;
                background: #7f8;
            }

            100% {
                width: 0%;
                background: #F69;
            }
        }


        .buttonswrapper {
            width: 100%;
            bottom: 0;
            position: absolute;
            background: radial-gradient(circle at 30% 60%, #4CAF5055, #449e4855 50%);
            background-color: #7CAF80;
            padding: 4px 0 5px 0;
            margin: -2px;
            text-align: center;
            min-height: 172px;
            max-height: 60%;
        }

        #buttons {
            width: 100%;
            border-radius: 16px;
            display: inline-block;
            bottom: 0;
            background: radial-gradient(circle at 30% 60%, #4CAF5055 12%, #5bcF6055 50%);
            background-color: #7CAF80;


            padding: 1px 0 9px 0;
            max-width: 900px;
            max-height: 50%;
            /* min-width */
            text-align: center;
            /* max-height: 420px; */
        }

        button {
            cursor: pointer;
            filter: drop-shadow(0 0 8px #94af84);

            background-color: #4CAF50;
            /* Green */
            border: none;
            color: white;

            text-align: center;
            text-decoration: none;
            display: inline-block;


            font-size: 1.5rem;
            border: 2px solid #77dd9977;
            border-radius: 12px;
            background: radial-gradient(circle at 60% 30%, #27c927, #1aa531 90%);


            margin: 0;
            padding: 16px 5px;
            max-height: 60px;
            width: 32.5%;
            height: 24.2%;
            max-height: 78px;
            min-height: 38px;
        }

        html,
        body,
        *,
        .game {
            /* max-width:400px !important; */
        margin:auto !important;
        text-align: center;

        /* display:inline-block !important;  */
        }


        html,
        body {
            height: 100%;
            min-height: 500px;
            letter-spacing: 6px;
            margin: 0;
            padding: 0;
            text-align: center;
            touch-action: none !important;
            user-select: none;
            /* supported by Chrome and Opera */
            -webkit-user-select: none;
            /* Safari */
            -khtml-user-select: none;
            /* Konqueror HTML */
            -moz-user-select: none;
            /* Firefox */
            -ms-user-select: none;
            /* Internet Explorer/Edge */
        }


        input[type=number]::-webkit-inner-spin-button,
        input[type=number]::-webkit-outer-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }

        toptext,
        h1 {
            font-size: 1rem;
            /* line-height: 3.5rem;*/
            color: #fefafa;
            font-family: arial;
            white-space: pre;
            font-weight: bolder;

            display: block;
            width: 100%;

            position: fixed;
            margin: -15px auto 2px auto;
            text-align: center;
            /* font-size: 1rem;
            line-height: 4rem;
            color: #fefafa;
            font-family: arial;
            white-space: pre;
            padding-left: 5px;
            display: inline-block; */
        }

        toptext b {}

        .ang {
            /* transform: rotateZ(-1deg);
	*/
            margin-bottom: 1px;
            margin-top: 8px;
            margin-right: 0;
            margin-left: 0;
            padding: 0;
            filter: drop-shadow(-2px 0 3px #fee);
            /*
word-break: break-all;*/
            padding: 0;
        }

        body {
            font-family: "Trebuchet MS";
            color: #ccc;
            font-size: 1.1rem;
            /* min-height: 400px; */
            overflow: none;
            background: radial-gradient(circle at 40% 30%, transparent, #6c6c6c55 50%);

            /* background-color: #FFFFFF; */


            background-repeat: repeat;
            margin: 0;
            padding: 0;






        }

        * {
            box-sizing: border-box;
        }

        article {}

        i2 {
            background-color: #fae2d9;
            border-radius: 50%;
            padding: 1px 2px;
            color: #bca996;
            margin: 2px 4px;
            display: inline-block;
            z-index: -1;
            border: 2px solid #fed;
            /*white-space: nowrap;*/
            width: 50%;
            min-height: 120px;
            max-height: 220px;
            height: 20%;
            transition: all 0.5s ease-in-out;
            /*right:190px;*/
            font-size: 220%;
        }

        i2::before {
            content: '';
            after: '';
        }

        gr {
            color: #dfc7b6;
            font-size: 50%;
        }

        whc {
            color: #fff;
            /* font-size: 120%; */
            font-size: 220%;


        }

        .fo {
            opacity: 0.01;
            display: block;
            position: fixed;
            top: 10%;
            left: 0;
            width: 100%;
            height: 10%;
            /*margin: 0 -20px 50px -10px;*/
            /* transform: rotateZ(10deg);
	*/
            /*     transition: all 0.5s ease-in-out;*/
        }

        .fi {
            opacity: 1;
            margin: 1px;
            padding: 0;
            /*	transform: rotateZ(-1deg);
	 */
            display: block;
            animation-duration: 0.2s;

            animation-iteration-count: 1;
            animation-fill-mode: forwards;

            animation-timing-function: linear;
            animation-name: slidein;
        }


        @keyframes slidein {
            0% {
                opacity: 0;
                /* filter: hue-rotate(-20deg); */
                /* left:-230px; */

                /* filter: hue-rotate(0deg); */
                /* font-size: 300%; */

            }

            100% {
                opacity: 1;
                /* filter: hue-rotate(0deg); */
            }
        }

        .fa {
            opacity: 1;
            margin: 1px;
            padding: 0;
            /*	transform: rotateZ(-1deg);
	 */
            /* display:block; */
            animation-duration: .2s;

            animation-iteration-count: 1;
            animation-fill-mode: forwards;
            /* animation-play-state: paused; */
            animation-timing-function: ease-in-out;
            animation-name: slideout;
        }


        @keyframes slideout {
            0% {
                opacity: 0.6;
                /* left:0; */
                /* filter: hue-rotate(20deg); */
            }


            100% {
                /* left:-230px; */
                opacity: 0;
                /* filter: hue-rotate(0deg); */
                /* font-size: 30%; */
                /* top: -200px; */
            }
        }


        .redpow {
            animation-duration: 0.8s;
            animation-name: redpowani;
        }

        @keyframes redpowani {
            0% {
                filter: hue-rotate(-102deg);
            }

            100% {
                filter: hue-rotate(0deg);
            }
        }

        .greenpow {
            animation-duration: 0.8s;
            animation-name: greenpowani;
        }

        @keyframes greenpowani {
            0% {
                filter: hue-rotate(0deg);
            }

            10% {
                filter: hue-rotate(20deg);
            }

            100% {
                filter: hue-rotate(0deg);
            }
        }

        body::before {
            top: 0;
            left: 0;
            margin: 0;
            padding: 0;
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: radial-gradient(circle at 40% 30%, transparent, #dddedd55 50%);
        }

        .scorebar {
            display: inline-block;
            margin-top: 1px;
            margin-bottom: 6px;
            font-weight: normal;
            font-size: 80%;
            letter-spacing: 2px;
            /*transition: all 2s;*/
            max-width: 520px;
            text-align: center;
            position: relative;
            color: #ffffff;
        }

        b {
            padding-left: 14px;
            padding-right: 10px;
            letter-spacing: 0px;
        }

        /* .ang,
        i2,
        #answer {
          transition: all 0.5s ease-in-out;
   
        } */

        #scoring {
            background-color: #fafafa99;
            padding: 12px;
        }

        #hiscoring {
            background-color: #fafafacc;
            padding: 12px;
        }
    </style>
</head>

<body>

    <input type="hidden" class="number" pattern=[0-9]* id="answer" name="answer" />
    <!-- onkeyup="check();" autofocus tabindex="1" -->
    <span id="answer2"></span>
    <input type="hidden" value="" id="eval" />
    <div id="scoreoverlay" class="scoreoverlay">
        <div>🏹</div>
        <div class="wrapper">
            <spansmall>1000 Decimals of Pi !<br />
                How many can you crank <br />
                before time's up?<br />
            </spansmall>


        </div>
        <div id="scoring">
            SCORE <b id="score3"></b>
        </div>
        <div id="hiscoring">
            HISCORE <b id="hiscore3"></b>
        </div>
        <br />
        <button onclick="newround()">GO⚡️</button>

        <spansmall>
            <br />
            Made for Mobile<br />
            Coded to 99% on a mobile<br  />
            Mobile-XP first<br />

            <br />
            <br />
        
        </spansmall>
    </div>

  
    <toptext>
        <h1>MATH</h1>
    </toptext>
    <div class="scorebar">
        <span class=score>SCORE
            <b id="score"></b> </span>
        <span class=hiscore>
            HISCORE <b id="hiscore"></b>
        </span>
    </div>
    <div class="progressbarboss">
        <div id='timer'></div>
    </div>
    <div class="buttonswrapper">
        <div id="buttons">
        </div>
    </div>
    <div class="fb" id="fb"></div>
    <script>


        mobile = /Android|webOS|iPhone|iPad|iPod|BlackBerry/i.test(navigator.userAgent);
        eventtyper = mobile ? "touchstart" : "mousedown";


        diff = 0;
        arrayblaha = 1;
        delement3 = [];
        // ⭐️⭐️⭐️⭐️
        var start, previousTimeStamp;
        var timestamp;
        var counttime;
        var score = 0;
        var hiscore = 63;
        var maxcountime = 390;
        var pluscount = 103;
        var speedish = 0.055;
        var speedincrease = 0.000021;
        document.getElementById('score').innerHTML = score;
        document.getElementById('hiscore').innerHTML = hiscore;
        document.getElementById('score3').innerHTML = score;
        document.getElementById('hiscore3').innerHTML = hiscore;
        /*
        var globalprogress;
        
        function createProgressbar(id, duration, callback) {
          var progressbar = document.getElementById(id);
          progressbar.className = 'progressbar';
          var progressbarinner = document.createElement('div');
          progressbarinner.className = 'inner';
          
          globalprogress = progressbarinner;
          globalprogress.style.animationDuration = duration;
          if (typeof(callback) === 'function') { progressbarinner.addEventListener('animationend', callback);
          }
        progressbar.appendChild(progressbarinner);
        progressbarinner.style.animationPlayState = 'running';
        }
        */
        //addEventListener('load', function() {
        /*
        createProgressbar('progressbar1', '20s', function() {
      alert("GAME OVER • YOUR SCORE " + score);
      reset();
      //score=0;
      Array.from(document.getElementsByClassName("fo")).map(el =>{
      //alert('done');
      el.classList.remove('fi');
      //el.classList.add('fo')
      setTimeout(()=> el.remove(),380) 
      });
      }
      }); */
        /*
        createProgressbar('progressbar2', '19s');createProgressbar('progressbar3', '17s');createProgressbar('progressbar4', '15s');*/
        //});
        function check() {
            // window.setTimeout(document.getElementById('answer').focus(), 20);
            //  document.getElementById('answer').focus();
            answered = document.getElementById('answer').value;
            if (answered == document.getElementById('eval').value) {



                Array.from(document.getElementsByClassName("fi")).map(el => {
                    el.classList.add("fa");

                });

                //if(0){
                //score ⭐️⭐️⭐️⭐️⭐️⭐️⭐️
                next();
                score++;
                //sound.rate(0.99+Math.random()*0.01);
                soundx = sound.clone();
                soundx.attack = 0.6;
                soundx.volume = 0.4;
                /// hmmm meh
                //soundx.playbackRate = 0.9; // try something between 0.25 and 3
                //soundx.rate = 2;
                //440 + Math.ceil( 10* Math.random()); // a5
                soundx.play(0, 0);
                //globalprogress.style.animationDuration =  "16s";
                //globalprogress.style.animationDuration
                //document.documentElement.style.getProperty('--elapsed');
                //document.documentElement.style.setProperty('--elapsed', 10+'s');
                if (hiscore < score) {
                    hiscore++;
                }
                document.getElementById('score').innerHTML = score;
                document.getElementById('hiscore').innerHTML = hiscore;
                delement4 = document.getElementById('buttons');
                delement4.classList.add("greenpow");
                setTimeout(() => delement4.classList.remove('greenpow'), 500);
                //      document.documentElement.style.setProperty('--fbpowro', 6*4*2*Math.ceil(-33 + Math.random() * 60) + 'deg');

                let diffspin = elapsed - diff;
                diffspin = -1000 * Math.abs(400 / diffspin);
                // if(diffspin < 1){ diffspin = 1;}



                console.log(diffspin);
                // document.documentElement.style.setProperty('--fbpowro', 6 * 4 * 2 * Math.ceil(-33 + Math.random() * 60) + 'deg');
                document.documentElement.style.setProperty('--fbpowro', diffspin + 'deg');
                diff = elapsed;





                //  document.documentElement.style.setProperty('--fbpowoutho', Math.ceil(-1 + Math.random() * 10) + '%');
                arrayblaha++;
                // should work too resuse these.. shouldn't be more than 2..3.. unlikely 4 at once
                arrayblaha = arrayblaha % 3;
                console.log(arrayblaha);
                delement3[arrayblaha] = document.getElementById('fb').cloneNode();
                //              body.innerHTML += [arrayblaha];
                delement3[arrayblaha] = document.body.appendChild(delement3[arrayblaha]);
                //              delement3.innerHTML +=
                delement3[arrayblaha].innerHTML = "⭐️" + answered + "😀"; // 🏆🏅


                delement3[arrayblaha].classList.add("fbpow");
                // setTimeout(() => delement3[arrayblaha].classList.remove('fbpow'), 3000);




                //                LOTS OF ELEMENTS IF NOT DELETED?
                //setTimeout(() => delement3[arrayblaha].remove(), 1799);
                delement3.forEach(function (el) {
                    el.addEventListener("animationend", function () { el.remove(); }, false);

                });




                // correct
                Array.from(document.getElementsByClassName("fa")).map(el => {
                    el.addEventListener("animationend", function () { el.remove(); }, false);
                    // el.remove(); 
                });





                counttime = counttime + pluscount;
                speedish += speedincrease;

                document.getElementById('answer').value = '';
                document.getElementById('answer2').innerHTML = '';

            } else {

                delement2 = document.getElementById('buttons');
                delement2.classList.add("redpow");
                setTimeout(() => delement2.classList.remove('redpow'), 800);


                document.getElementById('answer').value = '';
                document.getElementById('answer2').innerHTML = '';
                //WRONG ! :)
                //document.getElementById('answer').value = ''; // ALSO MADE AUTOCHEck FOR FASTER action :)
                //document.getElementById('answer2').innerHTML = '';
            }
        }

        function makebuttons() {
            var arry = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0];
            arry.forEach(iok => {
                // operation
                document.getElementById('buttons').innerHTML += "<button class='numkey' value='" + iok + "'>" + iok + "</button>";
                if (iok == 9)
                    document.getElementById('buttons').innerHTML += "<button class='numkey' value='clear'>❌</button>";
                if (iok == 0)
                    document.getElementById('buttons').innerHTML += "<button id='check' value=''>⚡️</button>";
            });
            var elements = document.getElementsByClassName("numkey");
            var myFunction = function () {
                var attribute = this.getAttribute("value");
                //alert(attribute);
                if (attribute == "clear") {
                    document.getElementById('answer').value = '';
                    document.getElementById('answer2').innerHTML = '';
                } else {
                    // once there was multiple sequences of numbers here... but stripped that for more action
                    document.getElementById('answer').value += attribute;
                    document.getElementById('answer2').innerHTML += attribute;
                    check(); // AUTOCHEck :)
                }
            }
            for (var i = 0; i < elements.length; i++) {
                //click waits till released
                /*elements[i].on('touchstart mousedown', function(e) {
               e.preventDefault();
               myFunction();
           });*/
                elements[i].addEventListener(eventtyper, myFunction, false);
                // elements[i].addEventListener("mousedown", myFunction, false);



                //}
            }


            document.getElementById('check').addEventListener(eventtyper, check, false);
            //  document.getElementById('check').addEventListener("mousedown", check, false);


            // Hey logic here... should only be active in some cases when game has started.. 
            window.addEventListener("keydown", function (event) {
                if (event.defaultPrevented) {
                    return; // Do nothing if the event was already processed
                }

                // gamenotstarted... start
                if (start === undefined) {
                    newround();
                    // break;
                }
                document.getElementById('answer').value += event.key;
                document.getElementById('answer2').innerHTML += event.key;
                //  document.getElementById('answer').value += event.key;
                //  document.getElementById('answer2').innerHTML += event.key;
                check(); // AUTOCHEck :)

                return; // hmm breaks... contiunes


                switch (event.key) {




                    case "1": // IE/Edge specific value
                    case "1":
                    // Do something for "down arrow" key press.
                    /*
                          document.getElementById('answer').value += 1;
                           document.getElementById('answer2').innerHTML += 1;
                           check(); // AUTOCHEck :)
                           break;
   */


                    case "Down": // IE/Edge specific value
                    case "ArrowDown":
                        // Do something for "down arrow" key press.
                        break;
                    case "Up": // IE/Edge specific value
                    case "ArrowUp":
                        // Do something for "up arrow" key press.
                        break;
                    case "Left": // IE/Edge specific value
                    case "ArrowLeft":
                        // Do something for "left arrow" key press.
                        break;
                    case "Right": // IE/Edge specific value
                    case "ArrowRight":
                        // Do something for "right arrow" key press.
                        break;
                    case "Enter":
                        // Do something for "enter" or "return" key press.
                        break;
                    case "Esc": // IE/Edge specific value
                    case "Escape":
                        // Do something for "esc" key press.
                        break;
                    default:
                        return; // Quit when this doesn't handle the key event.
                }

                // Cancel the default action to avoid it being handled twice
                event.preventDefault();
            }, true);




        }
        const dl = () => {
            reset();
            makebuttons();
        }
        var q = z = w = 0;
        function evalQ(a) {
            try {
                return eval(a);
            } catch (error) {
                return error;
                //console.error(error);
            }
        }
        const v = (a) => {
            // setTimeout(() => {
            //     d = document.createElement("div");
            //     d.classList.add("fo");
            //     d.innerHTML = ('<div class="ang"><i3 id="' + w + 'b"><whc>' + a + '</whc></i3></div>');
            //     document.body.append(d);
            //     setTimeout(() => d.classList.add("fi"), 1)
            // }, 1 + w % 6);



            d = document.createElement("div");
            d.classList.add("fo");
            d.innerHTML = ('<div class="ang"><i3 id="' + w + 'b"><whc>' + a + '</whc></i3></div>');
            document.body.append(d);
            d.classList.add("fi");



            // d = document.createElement("div");
            // d.classList.add("fo");


            // d.innerHTML = (``);

            document.getElementById('eval').value = (evalQ(a));

            // document.body.append(d);
            // d.classList.add("fi");

            w++;
        }
        //if ar === undefined
        var ar = [];
        function c(po) {
            ar.push(po);
        }
        //v(ar.shift());	
        /*
        document.body.addEventListener('click', function(e){
        e.preventDefault();
        //alert(e.changedTouches[0].pageX) // alert pageX coordinate of touch point
        */
        function next() {

            //alert("next");
            // if (w % 1 == 0) {
            //     Array.from(document.getElementsByClassName("fo")).map(el => {
            //         //alert('done');
            //         //el.classList.remove('fi');
            //         //el.classList.add('fo')
            //         //el.style.height = "22px";
            //         el.style.marginTop = "-30px";
            //         el.style.opacity = "0";
            //         el.remove();
            //     });
            //     //return null; 
            // }








            if (ar.length > 0) {
                v(ar.shift())
                /*
                if(ar.length==0){
                setTimeout(()=> v("'done😀'"),131)
                }*/
            } else {
                //document.body.innerHTML
                reset();


                // Array.from(document.getElementsByClassName("fo")).map(el => {
                //     //alert('done');
                //     el.classList.remove('fi');
                //     //el.classList.add('fo')
                //     setTimeout(() => el.remove(), 80)
                // });
            }
        }
        /*, false)
        */
        document.addEventListener("DOMContentLoaded", dl);
        window.addEventListener('touchmove' || 'touchdowm' || 'touchend' || 'mousedown', ev => {
            //
            if (1) {
                ev.preventDefault();
                ev.stopImmediatePropagation();
            };
        }, { passive: false });
        const reset = () => {
            elapsed = 0;
            start = undefined;
            ar = [];
            // score = 0;
            document.getElementById('score').innerHTML = score;
            counttime = 300;
            counttime2 = 100;
            w = 0;
            //c(`4+4`);
            //c("7*2"); //
            /*	c("1+2"); //
                c("2+2"); //
                c("2+1"); //
                c("3+1"); //
                c("5+2"); //
                c("3+2"); //
            	
                c("3+1"); //
                c("1+5"); //
                c("1+2"); //
            	
                c("5+1"); //
                c("5+2"); //
                c("3+2"); //
                c("3+1"); //
                c("7+2"); //
                c("5+2"); //
                */
            /*string = ""+Math.PI;
            string = string.substring(2,28);
            string += string*3;
            string += string*5;
            op = 0;
            while(op<30){
        	
                c(string[op+2] +'+'+string[op+3]);
            	
               op++;
            }*/
            string = "14159265358979323846264338327950288419716939937510582097494459230781640628620899862803482534211706798214808651328230664709384460955058223172535940812848111745028410270193852110555964462294895493038196442881097566593344612847564823378678316527120190914564856692346034861045432664821339360726 024914127372458700660631558817488152092096282925409171536436 7892590360 0113305305 4882046652 1384146951 9415116094 3305727036 5759591953 0921861173 8193261179 3105118548 0744623799 6274956735 1885752724 8912279381 8301194912 9833673362 4406566430 8602139494 6395224737 1907021798 6094370277 0539217176 2931767523 8467481846 7669405132 0005681271 4526356082 7785771342 7577896091 7363717872 1468440901 2249534301 4654958537 1050792279 6892589235 4201995611 2129021960 8640344181 5981362977 4771309960 5187072113 4999999837 2978049951 0597317328 1609631859 5024459455 3469083026 4252230825 3344685035 2619311881 7101000313 7838752886 5875332083 8142061717 7669147303 5982534904 2875546873 1159562863 8823537875 9375195778 1857780532 1712268066 1300192787 6611195909 2164201989";
            string = string.replace(/\D/g, '');
            op = 0;
            while (op < 1000) {
                //	c(Math.ceil(op*0.1) +'+'+string[op]);
                mathie = string[op++] + "+" + string[op];
                if (eval(mathie) > 9) {
                    mathie = string[--op] + '-' + string[++op];
                }
                if (eval(mathie) < 0) {
                    mathie = string[--op];
                }
                //	c(Math.ceil(op*0.1)>
                c(mathie);
                op++;
            }
            v(ar.shift());
            ////// HÄÄÄÄR
            /// START
            startscreen();
        }
        function startscreen() {
            if (score > 0) {
                document.getElementById('score3').innerHTML = score;
            }
            document.getElementById('hiscore3').innerHTML = hiscore;


            setTimeout(() => document.getElementById('scoreoverlay').classList.add('show'), 2);
            //            document.getElementById('scoreoverlay').classList.add('show');

            //delement.classList.add("pewits");
        }
        function newround() { //startgame
            score = 0;
            // Array.from(document.getElementsByClassName("fo")).map(el => {
            //     el.classList.remove('fi');
            //     setTimeout(() => el.remove(), 380)
            // });



            delement = document.getElementById('scoreoverlay');
            //delement.classList.add("powit2");
            setTimeout(() => delement.classList.remove('show'), 280);
            //}
            // perhaps not reseting score until restart?
            reset();
            //var element = document.getElementById('progressbar2');
            function step(timestamp) {
                // 😀⭐️😀 gameloop
                if (start === undefined) {
                    start = timestamp;
                }
                //const 
                elapsed = timestamp - start;
                if (previousTimeStamp !== timestamp) {
                    // Math.min() is used here to make sure the element stops at exactly 200px
                    //counttime = Math.min(0.1 * elapsed, 0);
                    //counttime2 = Math.min(0.1 * elapsed, 0);
                    //counttime2 = 300-Math.min(0.1 * elapsed, 0);
                    counttime2 = counttime - Math.ceil(speedish * elapsed);
                    if (counttime2 > maxcountime) {
                        counttime = counttime - 10;
                        counttime2 = maxcountime;
                    }
                    //counttime--;
                    //element.style.transform = 'translateX(' + count + 'px)';
                    element = document.getElementById('timer');
                    element.style.width = counttime2 + 'px';
                    element.style.backgroundColor = colortohex(120 + counttime2 % 5, 190 + Math.ceil(counttime2 / 2) % 65, 120 + Math.ceil(counttime2 / 3) % 45);
                    //element.innerHTML = counttime2 +" "+elapsed;
                }
                //if (elapsed <200000) { // Stop the animation after 2 seconds
                //alert("done");
                if (counttime2 > 1) { // SHOULD BE TRUE TO ANIMATE
                    previousTimeStamp = timestamp
                    window.requestAnimationFrame(step);
                } else {
                    reset();
                    startscreen();
                }
            }
            window.requestAnimationFrame(step);
        }
        function colortohex(red, green, blue) {
            return '#' + red.toString(16) +
                green.toString(16) +
                blue.toString(16);
        }
    </script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/pizzicato/0.6.4/Pizzicato.js"></script>
    <script>
        var sound = new Pizzicato.Sound('https://s3-us-west-2.amazonaws.com/s.cdpn.io/3/success.mp3', function () {
            // Sound loaded!
            //sound.play();
        });
        var dubDelay = new Pizzicato.Effects.DubDelay({
            feedback: 0.42,
            time: 0.84,
            mix: 0.42,
            cutoff: 900
        });
        sound.addEffect(dubDelay);
        //sound.play();

        window.onbeforeunload = function (e) {
            return "Sure you want to leave?";
        };
    </script>

</body>

</html>
