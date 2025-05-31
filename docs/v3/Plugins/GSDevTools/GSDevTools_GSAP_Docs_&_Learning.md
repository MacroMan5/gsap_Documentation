# GSDevTools | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/GSDevTools](https://gsap.com/docs/v3/Plugins/GSDevTools)  
**Last Updated:** 2025-05-23T00:18:05.225Z  
**Extracted:** 2025-05-31 16:56:03

---

# GSDevTools | GSAP | Docs & Learning

```
<div class="credits"><a href="https://codepen.io/PointC/">Animation and Design by Craig Roblewsky</a></div>
<svg id="demo" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1500 1000">
  <title>May the morph be with you</title>
<defs>
<mask id="titleMask">
 <rect x="0" y="0" width="1500" height="1000" fill="#fff"  stroke-miterlimit="10"/>
 
 <rect class="topCut" x="0" y="-278" width="1500" height="360" fill="#000"  stroke-miterlimit="10"/>
 <rect class="bottomCut" x="0" y="840" width="1500" height="320" fill="#000"  stroke-miterlimit="10"/>
  </mask>
<mask id="bladeMask">
<rect id="bladeMaskRect" x="735" y="114" width="43" height="512" fill="#fff"/>
  </mask>
  
<symbol id="fighter">

    <path d="M53.5,152.44v-1.17l54.38-1.32h.22c.07,0,.15,0,.15-.07s.15-.07.22-.15a.26.26,0,0,1,.15-.07c.07-.07.07-.15.15-.15l.07-.15c0-.07.07-.15.07-.22v-.44a.27.27,0,0,0-.07-.22.26.26,0,0,0-.07-.15l-.15-.15c-.07-.07-.15-.07-.15-.15a.26.26,0,0,0-.15-.07.26.26,0,0,1-.15-.07h-.22l-54.38-1.32v-1.25a1,1,0,0,0-1-1H49.76a1,1,0,0,0-1,1v.15h-.51V109.88h4.84a1,1,0,0,0,1-1V95.71a.72.72,0,0,0-.29-.66l83.44-6.82c17.69-.44,22.16-3.67,22.6-4a1.18,1.18,0,0,0,.37-.81V80.16a1.18,1.18,0,0,0-.37-.81c-.44-.37-4.92-3.6-22.6-4l-83.51-7a1.09,1.09,0,0,0,.29-.66V54.54a1,1,0,0,0-1-1H48.14V17.93h.51v.15a1,1,0,0,0,1,1h2.79a1,1,0,0,0,1-1V16.82l54.16-1.32a.27.27,0,0,0,.22-.07H108a1.06,1.06,0,0,0,.66-.81v-.15h0V14.4h0a1,1,0,0,0-1-.88L53.57,12.2V11a1,1,0,0,0-1-1H49.76a1,1,0,0,0-1,1v.51H20.62a.5.5,0,0,0-.51.51v5.5a.5.5,0,0,0,.51.51h5.14l-.66,3.16a.79.79,0,0,0-.07.44L17.76,56.89H10.42V56.6a1.18,1.18,0,0,0-.37-.81.83.83,0,0,0-.81-.22L.88,56.67a1,1,0,0,0-.88,1v7a1,1,0,0,0,.88,1L9.25,67a1.05,1.05,0,0,0,.81-.22,1.18,1.18,0,0,0,.37-.81v-.22h5.43l-.51,2.5L11,72.38a.9.9,0,0,0-.51.81V89.92a.93.93,0,0,0,.07.44,1,1,0,0,0,.22.29h0L15.34,95l.51,2.42H10.42v-.22a1.18,1.18,0,0,0-.37-.81.83.83,0,0,0-.81-.22L.88,97.4a1,1,0,0,0-.88,1v7a1,1,0,0,0,.88,1l8.37,1.1a1.05,1.05,0,0,0,.81-.22,1.18,1.18,0,0,0,.37-.81v-.07h7.34L25,141.73a.79.79,0,0,0,.07.44l.66,3.16H20.62a.5.5,0,0,0-.51.51v5.5a.5.5,0,0,0,.51.51h28v.51a1,1,0,0,0,1,1H52.4A1,1,0,0,0,53.5,152.44Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="54 14.11 66.77 14.4 54 14.7 54 14.11" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="51.21" y="11.91" width="0.73" height="5.14" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="10.85" y="58.73" width="16.59" height="4.99" fill="#999" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M26.93,54.54v2.2H19.81l2.13-10.27H46v7H28A1,1,0,0,0,26.93,54.54Z" transform="translate(0.5)" fill="#7c1a0a" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="29.49" y="55.57" width="14.31" height="11.08" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="45.85" y="55.57" width="6.53" height="11.08" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M26.93,67.83H17.54l.44-2h9v1.83C26.93,67.68,26.93,67.75,26.93,67.83Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="46.51 44.42 22.81 44.42 28.24 17.93 46.44 17.93 46.44 44.42 46.51 44.42" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M31.26,15.87h-9V13.45H48.65v2.42Z" transform="translate(0.5)" fill="#b3b3b3" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="8.87 57.77 8.87 64.82 2.56 63.87 2.56 58.58 8.87 57.77" fill="#999" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="46.59 145.4 28.39 145.4 22.96 118.9 46.66 118.9 46.66 145.4 46.59 145.4" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="10.92" y="99.53" width="16.59" height="4.99" fill="#999" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M45.43,96.67H52v11.08H45.5V96.67Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="29.56" y="96.67" width="14.31" height="11.08" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M19.81,106.57h7.12v2.2a1,1,0,0,0,1,1H46v7H21.94Z" transform="translate(0.5)" fill="#7c1a0a" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M70.45,91l23.19-4,.51-.07h21.36V87a.9.9,0,0,0,.37.73h0L47,93.37a1.11,1.11,0,0,0-1,1.1h0v.07H28a1,1,0,0,0-1,1V97.4h-9l-.66-3.23a1.17,1.17,0,0,0-.59-.73L14,90.94H70.08A1,1,0,0,0,70.45,91Z" transform="translate(0.5)" fill="#7c1a0a" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="72.27 77.51 93.11 78.39 93.11 85 72.34 85.88 72.27 77.51" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="95.09" y="78.4" width="20.91" height="6.53" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="65.37 78.03 70.22 77.51 70.22 85.73 65.37 85.22 65.37 78.03" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M78.23,87.57,70.6,88.89,69.2,89H65.31l-5.14-2.5V85.15h0l.07-.07a4.18,4.18,0,0,0,1.69-3.45A4.35,4.35,0,0,0,60.1,78.1V76.85l5.14-2.5h3.89l1.32.07,7.63,1.32L71,75.46h-.59c-.07,0-.22,0-.22.07l-6.75.73a.74.74,0,0,0-.51.29,1,1,0,0,0-.15.44v9.61a.79.79,0,0,0,.15.44,1.18,1.18,0,0,0,.51.29l6.82.73h.15Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M58.63,83.75a.44.44,0,0,1-.29.07,2.14,2.14,0,0,1-.66.15,2.27,2.27,0,1,1,0-4.55.93.93,0,0,1,.44.07,1,1,0,0,1,.44.15c.07,0,.15.07.22.15s.15.07.22.15a2.29,2.29,0,0,1,1,1.83A2.41,2.41,0,0,1,58.63,83.75Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M60.69,74.29l-2,1-.07.07-.22.22a.26.26,0,0,0-.07.15,1.06,1.06,0,0,0-.15.51v1.1c-.15,0-.29-.07-.51-.07a4.33,4.33,0,0,0,0,8.66h.44V87a.79.79,0,0,0,.15.44.26.26,0,0,1,.07.15l.22.22c.07,0,.07.07.15.07l2,1H12.55V74.14H60.69Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M115.51,76.19v.15H94.23l-.51-.07-23.26-4H14.16l2.57-2.42H47l68.84,5.65A.81.81,0,0,0,115.51,76.19Z" transform="translate(0.5)" fill="#7c1a0a" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M143,85h0a1.06,1.06,0,0,0,.15-.51V78.84a1.36,1.36,0,0,0-.15-.51,2.65,2.65,0,0,0-.66-.88c10.35.66,14.53,2.42,15.78,3.16v2.13c-1.32.73-5.43,2.42-15.78,3.16A3.8,3.8,0,0,0,143,85Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M141,79.13v5a5.63,5.63,0,0,1-4,1.91l-18.42,1.54-1.1-1V76.63l1-1L137,77.22A5.87,5.87,0,0,1,141,79.13Z" transform="translate(0.5)" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="8.87 98.5 8.87 105.55 2.56 104.67 2.56 99.38 8.87 98.5" fill="#999" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <path d="M31.19,147.45H48.65v2.42H22.24v-2.42h9Z" transform="translate(0.5)" fill="#b3b3b3" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <polygon points="54 148.55 66.99 148.84 54 149.14 54 148.55" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>
    <rect x="51.21" y="146.28" width="0.73" height="5.14" fill="#e5e5e5" stroke="#3a3a3a" stroke-miterlimit="10"/>

  
  </symbol>
  
        <filter id="glow" name="glow">
      <fegaussianblur stdDeviation="3"/>
    </filter> 
  </defs>

<g id="name" mask="url(#titleMask)">
 
  <path id="svg" d="M625.64,244.56a3,3,0,0,0-2.85-2l-73.12.34q-52.86-1.64-15.63,29.21,66.64,58.42,65.4,113.53T534,451.44H250V363H438.61q58.2,1.65,14.81-32.5-71.57-65.81-60.88-120.94T460,154.45H706.4l67.46,228.09,68.28-228.09H961.23l-105.92,297H697.56ZM1157,363V302.94h93v148.5H1118.37q-48.33,0-87.41-17.17t-61.6-51.52q-22.52-34.35-22.52-84.12,0-35,13.47-62.42a126.81,126.81,0,0,1,37.33-45.66,164.83,164.83,0,0,1,54.81-27.15,236.33,236.33,0,0,1,65.92-8.95H1250v88.44h-93q-31.26,0-46.28,1.85a119.82,119.82,0,0,0-26.74,6.17,49.6,49.6,0,0,0-20.77,15q-9.05,10.7-10.49,37.84,1,26.33,10.49,37.64a44.91,44.91,0,0,0,23,15,170.39,170.39,0,0,0,28,5.14Q1128.65,363,1157,363Z" stroke="#ecce26" stroke-miterlimit="10" stroke-width="10"/>
  <path id="wars" d="M416.47,668l-23.83,87.89H333L250,548.55h73.67l31,89.62,27-89.62h67.72l31.51,89.62,21-89.62h73.67L504.91,755.93H445.16Zm127.94,87.89,68.22-207.38h103L785,755.93H706.55l-13.07-37.34H631.87L618.8,755.93ZM664.33,594.5,634.6,676.65h57.16Zm361.8,99.67h45.76q40.64,1.15,10.34-22.69-50-46-42.51-84.45t47.11-38.49H1250V610.3H1149.45q-36.91-1.15-10.91,20.39,46.53,40.79,45.67,79.28t-45.67,46H958.07a27.45,27.45,0,0,1-19.8-8.44L880.6,687.42v68.51h-75V548.55h135q25,2.3,41.07,13.21a63.46,63.46,0,0,1,23.55,29.3q5.74,27.57.57,42.51a53.16,53.16,0,0,1-18.1,25Q975.6,668,953.59,673.64a2,2,0,0,0-1,3.1l13.65,17.44h59.94M880.6,600.25v38.2h52.28a17.19,17.19,0,0,0,9-3.09q4.88-3.09,5.17-15.58-.72-11.92-5.82-15.73t-8.55-3.81Z" stroke="#ecce26" stroke-miterlimit="10" stroke-width="10"/>

  <text transform="translate(750 520)" text-anchor="middle" font-size="60" fill="#fff" letter-spacing="0.1em">MAY THE MORPH BE WITH YOU</text>

  </g>
    
<g class="theLines" stroke="#1eaae1" stroke-miterlimit="10" stroke-width="2" fill="none">
<line class="topCut smallLine topLine" x1="-1000" y1="82" x2="-1000" y2="82"  />
<line class="bottomCut smallLine bottomLine" x1="2500" y1="840" x2="2500" y2="840"/>
  </g> 
  <use xlink:href="#fighter" x="0" y="0" class="topFighter"/>
  <use xlink:href="#fighter" x="0" y="0" class="bottomFighter" />



   <g id="morphGroup" >
    <circle id="stage" cx="750" cy="500" r="375" fill="#e5e5e5"  stroke-miterlimit="10"/>
<circle id="stageOutline" cx="750" cy="500" r="370" fill="transparent" stroke="#1eaae1" stroke-width="10" stroke-miterlimit="10" stroke-dashoffset="0" stroke-dasharray="0" transform="rotate(-90 750 500)"/>
  <g id="saber">
    <g mask="url(#bladeMask)" >
     
     <g filter="url(#glow)">
      <path class = "blade" d="M765.16,133.91c-.14-4.81-3.54-8.76-7.83-8.91-4.46-.16-8.19,3.83-8.33,8.91l-6.07,500.52h28.3Z" fill="#1eaae1"/>
      </g>
     
    </g>
      <rect x="735.85" y="747.64" width="42.45" height="127.36" fill="#bebebe"/>
      <rect x="742.92" y="620.28" width="35.38" height="42.45" fill="#8c8c8c"/>
      <rect x="728.77" y="662.74" width="56.6" height="84.91" fill="#bebebe"/>
      <rect x="728.77" y="747.64" width="14.15" height="120.28" fill="#8c8c8c"/>
      <rect x="771.23" y="747.64" width="14.15" height="120.28" fill="#8c8c8c"/>
      <rect x="750" y="747.64" width="14.15" height="120.28" fill="#8c8c8c"/>
      <rect x="721.7" y="712.26" width="7.08" height="28.3" transform="translate(1450.47 1452.83) rotate(180)" fill="#cbcbcb"/>
      <rect x="721.7" y="648.58" width="7.08" height="14.15" transform="translate(1450.47 1311.32) rotate(180)" fill="#bebebe"/>
      <rect x="714.62" y="627.36" width="28.3" height="14.15" rx="1" ry="1" fill="#bebebe"/>
      <path d="M728.77,669.81V606.13h0a22.9,22.9,0,0,1,20.48,12.66l7.82,15.64,28.3,14.15v21.23Z" fill="#bebebe"/>
      <circle cx="764.15" cy="655.66" r="7.08" fill="#8c8c8c"/>

  </g>


     <g id="leia">
       <path id="leftBun" d="M532.78,631.6H501.54a35,35,0,0,1-35-35V403.4a35,35,0,0,1,35-35h31.23a35,35,0,0,1,35,35V596.6A35,35,0,0,1,532.78,631.6Z" fill="#503c1d"/>
      <path id="rightBun" d="M998.46,631.6H967.22a35,35,0,0,1-35-35V403.4a35,35,0,0,1,35-35h31.23a35,35,0,0,1,35,35V596.6A35,35,0,0,1,998.46,631.6Z" fill="#503c1d"/>
      <path id="leiaHead" d="M750,327.9c-100.64,0-182.22.44-182.22,101.08v198c2.55,33.16,16.26,63,40.13,80.65l94.4,69.81c29.18,21.58,66.2,21.58,95.38,0l94.4-69.81c23.87-17.65,37.58-47.49,40.13-80.65V429C932.22,328.35,850.64,327.9,750,327.9Z" fill="#f0b496"/>
      <path id="leiaRightEye" class="leiaEye" d="M831,530.37a20.25,20.25,0,1,0,20.25,20.25A20.24,20.24,0,0,0,831,530.37Z" fill="#323232"/>
      <path id="leiaLeftEye" class="leiaEye" d="M669,530.37a20.25,20.25,0,1,0,20.25,20.25A20.24,20.24,0,0,0,669,530.37Z" fill="#323232"/>
      <path id="leiaNose" d="M735.18,638.34V578.6a.5.5,0,0,1,.5-.5h19.25a.5.5,0,0,1,.5.5v59.74a.5.5,0,0,1-.5.5H735.68A.5.5,0,0,1,735.18,638.34Z" fill="#ba8d79"  />
     
      <path id="leiaHair" d="M952,394.66l2.18-6-3-3C939.62,284.79,854,206.42,750,206.42c-104.52,0-190.52,79.19-201.32,180.84l-1.15,1.38.79,2.38c-.51,5.89-.79,11.84-.79,17.87l6.33-1.27,13.92,41.76,40.49,20.25,141.73-81,141.73,81,40.49-20.4,15-41.4,5.27,1.05C952.47,404.1,952.29,399.36,952,394.66Z" fill="#503c1d"/>
    </g>

    <g id="luke">
      <path id="leftSideHair" d="M531.53,444.79v16.62L458.71,611h54.62L458.71,677.5H758.16c-1.9-137.95-6.15-276.28-8.34-414.18C629.25,263.4,531.53,334.68,531.53,444.79Z" fill="#be9664"/>
      <path id="rightSideHair" d="M986.67,611h54.62l-72.82-149.6V444.79c0-110.16-97.81-181.46-218.47-181.46h-.18c2.19,137.9,6.44,276.23,8.34,414.18h283.13L986.67,611Z" fill="#be9664"/>
      <path id="lukeHead" d="M984.67,440.83H947.23V421.11c0-98-88.3-177.51-197.23-177.51S552.77,323.08,552.77,421.11v19.72H515.33a2,2,0,0,0-2,2V576.89a2,2,0,0,0,2,2h37.45v74.95a78.89,78.89,0,0,0,33.65,64.63l5.8,4.06L704.76,801.3a78.9,78.9,0,0,0,90.49,0l112.54-78.78,5.8-4.06a78.89,78.89,0,0,0,33.65-64.63V578.89h37.45a2,2,0,0,0,2-2V442.83A2,2,0,0,0,984.67,440.83Z" fill="#f0b496"/>
      <path id="lukeLeftEye" class="lukeEyes" d="M671.11,519.72a19.72,19.72,0,1,0,19.72,19.72A19.71,19.71,0,0,0,671.11,519.72Z" fill="#2980b9"/>
      <path id="lukeRightEye" class="lukeEyes" d="M828.89,519.72a19.72,19.72,0,1,0,19.72,19.72A19.71,19.71,0,0,0,828.89,519.72Z" fill="#2980b9"/>
      <path id="lukeNose" d="M730.28,636.88V520.22a.5.5,0,0,1,.5-.5H749.5a.5.5,0,0,1,.5.5V636.88a.5.5,0,0,1-.5.5H730.78A.5.5,0,0,1,730.28,636.88Z" fill="#ba8d79"  />
      <path id="lukeTopHair" d="M947.23,516.34,923,455.67l-75.79-25.15L769.72,325.93l-.54.14.54,10.11L741,432.57l-80,24.61L708.2,325.93,652.83,430.52,577,455.67l-24.27,60.68-5.63-39.45H473.88L533,358.56H493.6l47.47-54.16,27.69-52.29,125.09-67.67L750,214.16l56.15-29.73,125.09,67.67,27.69,52.29,47.47,54.16H967l59.17,118.34H952.86Z" fill="#be9664"/>
      <path id="dimple" d="M759.86,786a9.86,9.86,0,1,1-9.86-9.86A9.86,9.86,0,0,1,759.86,786Z" fill="#ba8d79"  />
    </g>

 <g id="darth">
    <path id="darthHead" d="M1006.15,692.13c5.18-4,17.88-7.94,22.67-12.2L942.11,474s-77-230.13-172-230.13H729.86c-95,0-172,230.13-172,230.13L471.18,679.92c4.79,4.26,17.49,8.18,22.67,12.2Z" fill="#323232"/>


    <path id="darthHelmet" d="M942.11,436V399.82c0-93-73.86-168.54-166.08-171.67a23.85,23.85,0,0,0-18-8.3H742a23.85,23.85,0,0,0-18,8.3c-92.23,3.13-166.08,78.68-166.08,171.67V436L461.83,692.13h32l84.5-205.7C600,432.21,630.09,409.1,678.86,409.1c33.35,0,54,26,55.13,26.87h32c1.14-.84,21.78-26.87,55.13-26.87,48.77,0,78.82,23.1,100.48,77.25l84.53,205.78h32Z"/>
    <path id="helmetHighlight" d="M605.7,387.95a7.48,7.48,0,0,1-7.49-7.49A112.4,112.4,0,0,1,710.5,268.18a7.49,7.49,0,1,1,0,15,97.42,97.42,0,0,0-97.31,97.31A7.48,7.48,0,0,1,605.7,387.95Z" fill="#1a1a1a"/>
              <path id="leftTriangle" d="M734,532l-80,112.07L589.91,532Z" fill="#505050"/>
    <path id="rightTriangle" d="M766,532H910.09l-64,112.07Z" fill="#505050"/> 
    <path id="maskBase" d="M885.4,680.2,910.09,532l-64,112.07-64-89.65V548a32,32,0,0,0-64,0v6.4l-64,89.65L589.91,532,614.6,680.2a31.91,31.91,0,1,0,42.89,43.94h185A31.91,31.91,0,1,0,885.4,680.2Z"/>
    <g id="maskVerticals">
      <polygon points="685.96 692.13 717.98 692.13 717.98 607.96 685.96 651.87 685.96 692.13" fill="#323232"/>
      <polygon points="782.02 607.96 782.02 692.13 814.04 692.13 814.04 651.87 782.02 607.96" fill="#323232"/>
      <rect x="733.99" y="596.07" width="32.02" height="96.06" fill="#323232"/>
    </g>
     <path id="darthLeftEye" d="M605.91,496c0-11,5.92-27.1,13.17-35.77,0,0,20.28-24.27,61.54-24.27a73.43,73.43,0,0,1,35.53,9C726,451,734,465,734,476v30c0,5.5-9.61,10-21.35,10H627.26C615.52,516,605.91,507,605.91,496Z"/>
    <path id="darthRightEye" d="M872.74,516H787.36c-11.74,0-21.35-4.5-21.35-10V476c0-11,8-25,17.83-31a73.43,73.43,0,0,1,35.53-9c41.26,0,61.55,24.27,61.55,24.27,7.24,8.67,13.16,24.76,13.16,35.77S884.48,516,872.74,516Z"/>
    <g id="highlights">
      <path d="M629.93,692.13a16,16,0,1,0,16,16A16,16,0,0,0,629.93,692.13Zm240.14,0a16,16,0,1,0,16,16A16,16,0,0,0,870.07,692.13ZM750,532a16,16,0,0,0-16,16v16h32V548A16,16,0,0,0,750,532Z" fill="#fff"/>
    </g>

  </g>

  <g id="chewie">
    <path id="chewieHead" d="M750,195.11c-106.35,0-198.2,117.46-205.62,228.54l-35.09,285H990.71l-35.09-285C948.2,312.56,856.35,195.11,750,195.11Z" fill="#503c1d"/>
    <path id="chewieFace" d="M958.61,708.61,935.08,468.54c-4.6-46.91-45.74-79.42-88.8-70.17h0l48.14-68.94L798.14,363.9,846.28,295l-64.19,17.24,16-68.94L750,312.19l-48.14-68.94,16,68.94L653.72,295l48.14,68.94-96.28-34.47,48.14,68.94h0c-43.06-9.25-84.2,23.26-88.8,70.17L541.39,708.61H628l25.68,64.19,32.09-48.14,32.09,80.24L750,724.66l32.09,80.24,32.09-80.24,32.09,48.14L872,708.61Z" fill="#a57d52"/>
    
    <path id="nose" d="M750,512.34c24.54,0,44.44,11.6,44.44,25.92a15.65,15.65,0,0,1-.83,4.81A21.82,21.82,0,0,0,765,562.57a70.21,70.21,0,0,1-30,0,21.82,21.82,0,0,0-28.63-19.5,15.7,15.7,0,0,1-.83-4.81C705.56,523.95,725.46,512.34,750,512.34Z" fill="#323232"/>
    <path id="noseShadow" d="M750,564.19l16-16c65.19,0,88.26,64.19,88.26,64.19H645.69s27.58-64.19,88.26-64.19Z" fill="#503c1d" opacity="0.35"/>
    <path id="chewieRightEye" d="M782.09,468.26A31.74,31.74,0,0,0,813.84,500h64.54s-31-63.48-64.54-63.48C796.86,436.52,782.09,450.73,782.09,468.26Z" fill="#503c1d"/>
    <path id="chewieLeftEye" d="M717.91,468.26A31.74,31.74,0,0,1,686.16,500H621.62s31-63.48,64.54-63.48C703.14,436.52,717.91,450.73,717.91,468.26Z" fill="#503c1d"/>
    <g id="chewieEyes">
    <circle id="chewieRightPupil" cx="814.19" cy="467.91" r="12.04" fill="#fff"/>
    <circle id="chewieLeftPupil" cx="685.81" cy="467.91" r="12.04" fill="#fff"/>
    </g>
    <path id="chewieMouth" d="M860.83,644.42H639.17a1.5,1.5,0,0,1-1.5-1.5V597.78a1.5,1.5,0,0,1,1.5-1.5H860.83a1.5,1.5,0,0,1,1.5,1.5v45.14A1.5,1.5,0,0,1,860.83,644.42Z" fill="#323232"/>
    <g id="chewieTeeth">
      <polygon class="botTeeth" points="685.81 644.42 701.86 612.33 717.91 644.42 685.81 644.42" fill="#fff"/>
      <polygon class="botTeeth" points="782.09 644.42 798.14 612.33 814.19 644.42 782.09 644.42" fill="#fff"/>
      <polygon class="upperTeeth" points="846.28 596.28 830.24 628.38 814.19 596.28 846.28 596.28" fill="#fff"/>
      <polygon class="upperTeeth" points="685.81 596.28 669.76 628.38 653.72 596.28 685.81 596.28" fill="#fff"/>
    </g>
  </g>
  
  
  
    <g id="r2d2">

      <path id="r2Head" d="M736.44,264.57c-150.86,7.1-266.92,137.05-266.92,288.08v100a43.15,43.15,0,0,0,43.15,43.15H987.33a43.15,43.15,0,0,0,43.15-43.15V544.73C1030.48,385.33,897.51,257,736.44,264.57Z" fill="#bebebe"/>
      <path id="topRightBlue" d="M760.79,264.81v85.74H952.1A279.36,279.36,0,0,0,760.79,264.81Z" fill="#2980b9"/>
      <path id="topLeftBlue" d="M739.21,264.81A279.36,279.36,0,0,0,547.9,350.55H739.21Z" fill="#2980b9"/>
      <path id="eyeBase" d="M854.57,523.15H731.73a21.58,21.58,0,0,1-21.36-24.63l15.41-107.88a21.58,21.58,0,0,1,21.36-18.52h92a21.58,21.58,0,0,1,21.36,18.52l15.41,107.88A21.58,21.58,0,0,1,854.57,523.15Z" fill="#2980b9"/>
      <path id="bottomStripe" d="M469.52,652.6a42.92,42.92,0,0,0,3.06,15.73h554.84a42.92,42.92,0,0,0,3.06-15.73V633.27h-561Z" fill="#2980b9"/>
      <path id="r2Eye" d="M847.09,447.64a53.94,53.94,0,1,1-53.94-53.94A53.94,53.94,0,0,1,847.09,447.64Z" fill="#323232"/>
      <circle id="r2EyeHighlight" cx="782.36" cy="436.85" r="21.58" fill="#fff" opacity="0.5"/>
      <g id="decals">
        <path d="M599,609.45H469.52v-56.8a294.1,294.1,0,0,1,1.55-29.5H599Z" fill="#2980b9"/>
        <path d="M1029.36,523.15c.54,7.15,1.12,14.29,1.12,21.58v64.73H1008.9v-86.3Z" fill="#2980b9"/>
        <path d="M750,609.45H706.85V544.73H750Z" fill="#2980b9"/>
        <path d="M879.45,609.45H771.58V544.73H879.45Z" fill="#2980b9"/>
        <path d="M620.55,566.3h64.73v43.15H620.55Z" fill="#505050"/>
        <path d="M620.55,523.15h64.73V566.3H620.55Z" fill="#505050"/>
        <path d="M987.33,566.3a43.15,43.15,0,1,1-43.15-43.15A43.15,43.15,0,0,1,987.33,566.3Z" fill="#8c8c8c"/>
        <path d="M971.14,566.3a27,27,0,1,1-27-27A27,27,0,0,1,971.14,566.3Z" fill="#fff"/>
        <path d="M857.88,577.09a21.58,21.58,0,1,1-21.58-21.58A21.58,21.58,0,0,1,857.88,577.09Z" fill="#c0392b"/>
      </g>

    <g opacity="0.5">
      <path d="M523.25,490.79a10.81,10.81,0,0,1-10.35-13.86,257.25,257.25,0,0,1,47.91-90.06,10.79,10.79,0,1,1,16.69,13.67,235.3,235.3,0,0,0-43.91,82.54A10.81,10.81,0,0,1,523.25,490.79Z" fill="#fff"/>
    </g>
  </g>
  </g>
</svg>
```

```
* {
  box-sizing: border-box;
}

body {
  height: 98vh;
  width: 100%;
  padding: 0;
  margin: 0;
  overflow: hidden;
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
  display: flex;
  align-content: center;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/314556/nightSky.jpg") center center repeat;
}

#demo {
  overflow: visible;
  opacity: 0;
  visibility: hidden;
  max-height: 80%;
}

#playIt {
  position: absolute;
  bottom: 20px;
  right: 20px;
  padding: 12px;
  cursor: pointer;
  font-family: 'Roboto', sans-serif;
  font-weight: 700;
  text-transform: uppercase;
}

.credits {
  color:#aaa;
  font-size:12px;
  margin-top:-60px;
}

a:hover, a:visited, a:link, a:active {
  color:#aaa;
  text-decoration:none;
}
```

```
gsap.defaults({ease:"power3.inOut"});
  
var master = gsap.timeline({delay:0.5, repeat:-1, repeatDelay:0.5});
var mt = 0.85;
var es = "power2.out";

gsap.set("#demo", {autoAlpha:1}); 
gsap.set(".bottomFighter", {rotation:180, y:758, transformOrigin:"center center"});
gsap.set("#stage, #luke, #darth, #chewie, #r2d2", {autoAlpha:0});

function flyBy() {
  var tl = gsap.timeline({defaults:{duration:2}});
  tl.add("fighter");
  tl.from(".bottomFighter, .topFighter", {duration:0.1, autoAlpha:0}, "fighter");
  tl.fromTo(".topFighter", {x:-1000}, {x:2500, ease:"none"}, "fighter");
  tl.fromTo(".bottomFighter", {x:2500}, {x:-1000, ease:"none"}, "fighter");
  tl.to(".topLine", {attr:{x2:2500}, ease:"none"}, "fighter");
  tl.to(".bottomLine", {attr:{x1:-1000}, ease:"none"}, "fighter");
  tl.to(".bottomFighter, .topFighter", {duration:0.1, autoAlpha:0}, "-=0.1");
  tl.to(".topCut", {y:418, ease:es}, "vanish");
  tl.to(".bottomCut", {y:-341, ease:es}, "vanish");
  tl.to(".smallLine", {duration:1, attr:{x1:749, x2:751}, ease:es});
  return tl;
}

function bladeCut() {
  var tl = gsap.timeline(); 
  tl.from("#saber path, #saber rect, #saber circle",  {duration:0.6, scale:0, transformOrigin:"center center", ease:"elastic(1, 0.5)", stagger:0.05}, );
  tl.from("#bladeMaskRect", {duration:0.8, y:512});
  tl.to("#saber", {duration:2, rotation:360, svgOrigin:"750 500"}, "spin");
  tl.from("#stageOutline", {duration:2, drawSVG:0}, "spin");
  tl.to("#bladeMaskRect", {y:512, ease:es});
  tl.to("#saber",  {duration:0.25, autoAlpha:0, ease:"none"});
  return tl;
}
  
function leiaStage() {
  var tl = gsap.timeline();
  tl.to("#stage", {autoAlpha:1});
  tl.from("#leia path", {duration:1.1, scale:0, transformOrigin:"center center", ease:"elastic(1, 0.5)", stagger:0.15});
  tl.to(".leiaEye", {duration:0.15, scaleY:0, repeat:3, yoyo:true, transformOrigin:"center center"});
  return tl;
}   

function leiaToLuke() {
  var tl = gsap.timeline({defaults:{duration:mt}});
  tl.to("#leiaHead", {morphSVG:"#lukeHead"}, 0);
  tl.to("#leftBun", {morphSVG:"#leftSideHair", fill:"#be9664"}, 0);
  tl.to("#rightBun", {morphSVG:"#rightSideHair", fill:"#be9664"}, 0);
  tl.to("#leiaHair", {morphSVG:"#lukeTopHair", fill:"#be9664"}, 0);
  tl.to("#leiaNose", {morphSVG:"#lukeNose", fill:"#ba8d79"}, 0);
  tl.to("#leiaLeftEye", {morphSVG:"#lukeLeftEye", fill:"#2980b9"}, 0);
  tl.to("#leiaRightEye", {morphSVG:"#lukeRightEye", fill:"#2980b9"}, 0);
  tl.set("#luke", {autoAlpha:1});
  tl.set("#leia", {autoAlpha:0});
  tl.from("#dimple", {duration:0.25, autoAlpha:0, ease:es});
  tl.to(".lukeEyes", {duration:0.25, x:-30});
  tl.to(".lukeEyes", {duration:0.45, x:30}, "+=0.25");
  tl.to(".lukeEyes", {duration:0.25, x:0}, "+=0.25");
  return tl;
}
  
function lukeToDarth() {
  var tl = gsap.timeline({defaults:{duration:mt}});
  tl.to("#lukeHead", {morphSVG:"#darthHead", fill:"#323232"}, 0);
  tl.to("#leftSideHair", {morphSVG:"#leftTriangle", fill:"#505050"}, 0);
  tl.to("#rightSideHair", {morphSVG:"#rightTriangle", fill:"#505050"}, 0);
  tl.to("#lukeTopHair", {morphSVG:"#darthHelmet", fill:"#000"}, 0);
  tl.to("#lukeLeftEye", {morphSVG:"#darthLeftEye", fill:"#000"}, 0);
  tl.to("#lukeRightEye", {morphSVG:"#darthRightEye", fill:"#000"}, 0);
  tl.to("#lukeNose", {morphSVG:"#rightTriangle", fill:"#505050"}, 0);
  tl.to("#dimple", {morphSVG:"#leftTriangle", fill:"#505050"}, 0);
  tl.set("#darth", {autoAlpha:1});
  tl.set("#luke", {autoAlpha:0});
  tl.from("#maskBase", {scale:0, transformOrigin:"center center", ease:es});
  tl.from("#maskVerticals", {duration:0.35, scaleY:0, transformOrigin:"center bottom", ease:es }, "-=0.1");
  tl.from("#helmetHighlight, #highlights", {duration:0.35, autoAlpha:0, ease:"none"});
  return tl;
}
  
function darthToChewie() {
  var tl = gsap.timeline({defaults:{duration:mt}});
  tl.to("#darthHead", {morphSVG:"#chewieHead", fill:"#503c1d"}, 0);
  tl.to("#darthHelmet", {morphSVG:"#chewieFace", fill:"#a57d52"}, 0);
  tl.to("#leftTriangle", {morphSVG:"#nose", fill:"#323232"},0);
  tl.to("#rightTriangle", {morphSVG:"#noseShadow", fill:"#503c1d", opacity:0.35}, 0);
  tl.to("#darthLeftEye", {morphSVG:"#chewieLeftEye", fill:"#503c1d"}, 0);
  tl.to("#darthRightEye", {morphSVG:"#chewieRightEye", fill:"#503c1d"}, 0);
  tl.to("#maskBase", {morphSVG:"#chewieMouth", fill:"#323232"}, 0);
  tl.to("#maskVerticals, #helmetHighlight, #highlights", 0.25, {autoAlpha:0 }, 0.25);
  tl.to("#chewie", 0.75, {autoAlpha:1, ease:"none"});
  tl.from(".botTeeth", 0.35, {scaleY:0, transformOrigin:"center bottom"}, "teeth");
  tl.from(".upperTeeth", 0.35, {scaleY:0, transformOrigin:"center top"}, "teeth");
  tl.set("#darth", {autoAlpha:0});
  return tl;
} 

function chewieToR2() {
  var tl = gsap.timeline({defaults:{duration:mt}});
  tl.to(".botTeeth", {duration:0.35, scaleY:0, transformOrigin:"center bottom"}, 0);
  tl.to(".upperTeeth", {duration:0.35, scaleY:0, transformOrigin:"center top"}, 0);
  tl.to("#chewieEyes", {duration:0.25, autoAlpha:0, ease:Linear.easeNone}, 0);
  tl.to("#chewieFace", {morphSVG:"#r2Head", fill:"#bebebe"}, 0);
  tl.to("#chewieHead", {morphSVG:"#r2Head", fill:"#bebebe"}, 0);
  tl.to("#nose", {morphSVG:"#eyeBase", fill:"#2980b9"},0);
  tl.to("#noseShadow", {morphSVG:"#r2Eye", fill:"#323232", opacity:1}, 0);
  tl.to("#chewieLeftEye", {morphSVG:"#topLeftBlue", fill:"#2980b9"}, 0);
  tl.to("#chewieRightEye", {morphSVG:"#topRightBlue", fill:"#2980b9"}, 0);
  tl.to("#chewieMouth", {morphSVG:"#bottomStripe", fill:"#2980b9"}, 0);
  tl.to("#r2d2", {duration:0.75, autoAlpha:1, ease:Linear.easeNone});
  tl.set("#chewie", {autoAlpha:0});
  tl.from("#decals path", {duration:0.9, scale:0, transformOrigin:"center center", ease:"elastic(1, 0.5)", stagger:0.1});
  tl.to("#r2EyeHighlight", {duration:0.4, x:20, y:20, repeat:1, repeatDelay:0.8, yoyo:true, ease:"pwer2.inOut"});
  return tl;
}
  
function ending() {
  var tl = gsap.timeline();
  tl.to("#r2d2", {autoAlpha:0});  
  tl.to("#stage, #stageOutline", {duration:1, attr:{r:0}, ease:"power3.in"}, 0);
  return tl;
} 

  
master.from("#name", 2, {autoAlpha:0, ease:"none"});
master.add( flyBy() );
master.add( bladeCut() );
master.add( leiaStage() );
master.add( leiaToLuke(), "+=0.5" );
master.add( lukeToDarth(), "+=0.5" );
master.add( darthToChewie(), "+=1" );
master.add( chewieToR2(), "+=1" );
master.add( ending(), "+=1" );

GSDevTools.create({paused:true, id:"SVG Wars"});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
