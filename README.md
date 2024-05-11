<div><svg id="wave" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 362.89 65.69" preserveAspectRatio="none">
    <path class="st0" d="M0,30.76c0,0,24.49-26.11,64.33-26.11c43.59,0,104.58,54.91,145.23,54.91s49.6-16.94,87.48-16.94s65.84,16.94,65.84,16.94v6.13H0V30.76z"/>
  </svg>
  <script>
    const wavePath = document.querySelector("#wave path");
    const duration = 2000; 
    let currentState = 0;

   const waveStates = [
     [
       { x: 64.33, y: 10 },
       { x: 134.23, y: 60 },
       { x: 200, y: 20 }, 
       { x: 278.35, y: 45 },
       { x: 362.89, y: 15 }
     ],
     [
       { x: 64.33, y: 60 },
       { x: 134.23, y: 10 },
       { x: 200, y: 20 },
       { x: 278.35, y: 40 },
       { x: 362.89, y: 20 }
     ],
     [
       { x: 64.33, y: 60 },
       { x: 134.23, y: 10 },
       { x: 200, y: 40 },
       { x: 278.35, y: 25 },
       { x: 362.89, y: 60 }
     ],
   ];

    function interpolateValues(from, to, progress) {
      return from + (to - from) * progress;
    }

    function updatePath(progress) {
      const from = waveStates[currentState];
      const to = waveStates[(currentState + 1) % waveStates.length];
      const points = from.map((point, index) => {
        return {
          x: interpolateValues(point.x, to[index].x, progress),
          y: interpolateValues(point.y, to[index].y, progress)
        };
      });

      const fixedStart = { x: 0, y: 65.69 };
      const fixedEnd = { x: 362.89, y: 65.69 };

      const pathData = `
        M0,${points[0].y}
        C${points[0].x},${points[0].y} ${points[1].x},${points[1].y} ${points[2].x},${points[2].y}
        S${points[3].x},${points[3].y} ${points[4].x},${points[4].y}
        V${fixedEnd.y} H0 Z
      `;
      wavePath.setAttribute("d", pathData);
    }

    function animateWave(timestamp) {
      const startTime = performance.now();
      function frame(now) {
        const elapsed = now - startTime;
        const progress = Math.min(elapsed / duration, 1);
        updatePath(progress);

        if (progress < 1) {
          requestAnimationFrame(frame);
        } else {
          currentState = (currentState + 1) % waveStates.length;
          animateWave();
        }
      }
      requestAnimationFrame(frame);
    }

    animateWave();
  </script>
</div>

<h2 align="left">My stack:</h2>
<div style="display: flex; align-items: flex-start; align: center">
<table align="center">
  <tr>
     <td align="center"  width="96">
        <img src="https://skillicons.dev/icons?i=html" width="48" height="48" alt="HTML5" />
      <br>HTML5
    </td>
    <td align="center" width="96">
        <img src="https://skillicons.dev/icons?i=css" width="48" height="48" alt="css" />
      <br>CSS
    </td>
<td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/sass-icon.svg" width="48" height="48" alt="Sass" />
      <br>Sass
    </td>
    <td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/js-icon.svg" alt="icon" width="65" height="65" />
      <br>JavaScript
    </td>
    <td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/ts-icon.svg" alt="icon" width="65" height="65" />
      <br>TypeScript
    </td>
    <td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/react-icon.svg" alt="icon" width="65" height="65" />
      <br>React
    </td>
        <td align="center" width="96">
        <img src="https://skillicons.dev/icons?i=nodejs" width="48" height="48" alt="Nodejs" />
      <br>Nodejs
      </td>
    <td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/webpack-icon.svg" alt="icon" width="65" height="65" />
      <br>Webpack
    </td>
  </tr>
   <td align="center" width="96">
        <img src="https://skillicons.dev/icons?i=babel" width="48" height="48" alt="css" />
      <br>Babel
    </td>
   <td align="center" width="96">
        <img src="https://skillicons.dev/icons?i=vite" alt="icon" width="48" height="48" />
      <br>Vite
    </td>
    <td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/github-icon.svg" alt="icon" width="65" height="65" />
      <br>Github
    </td>
    <td align="center" width="96"> 
        <img src="https://user-images.githubusercontent.com/25181517/192108372-f71d70ac-7ae6-4c0d-8395-51d8870c2ef0.png" width="48" height="48" alt="Git" />
      <br>Git
    </td>
    <td align="center"  width="96">
        <img src="https://skillicons.dev/icons?i=bootstrap" width="48" height="48" alt="bootstrap" />
      <br>Bootstrap
    </td>
    <td align="center" width="96">
        <img src="https://skillicons.dev/icons?i=jquery" width="48" height="48" alt="jQuery" />
      <br>jQuery
    </td>
      </td>
            <td align="center" width="96">
        <img src="https://skillicons.dev/icons?i=vscode" width="48" height="48" alt="VsCode" />
      <br>VsCode
    </td>
   <td align="center" width="96">
        <img src="https://techstack-generator.vercel.app/restapi-icon.svg" alt="icon" width="65" height="65" />
      <br>Rest API
    </td>
</table>
</div>
