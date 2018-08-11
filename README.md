# C3D-and-devicemotion
3D旋转与摇一摇触发

HTML陀螺仪：又称角速度传感器，是不同于加速度计（G-sensor）
1、陀螺仪角度：
z轴为轴：alpha的作用域为（0,360）
x轴为轴，beta的作用域为（-180,180）
y轴为轴，gamma的作用域为（-90,90）



3D基础：
transform-style:preserve-3d;
transform:perspective(25rem);
transform-origin:50% 50%;
transform:rotateY(30deg) translateZ(230px);


摇一摇触发：
1、devicemotion----设备的物理方向信息，表示为一系列本地坐标系的旋角
2、deviceorientation----提供设备的加速信息
3、compassneedscalibration---用于通知web站点使用罗盘信息校准上述事件

获取旋转角度
window.addListener("deviceorientation",yaoyiyao,true);
function yaoyiyao(event){
//处理event.alpha、event.beta、event.gamma
}
获取罗盘校准
window.addListener("compassneedscalibration",funtion(){
event.preventDefault();//阻止默认行为
alert("你的罗盘需要校准");
},true);
获取重力加速度（摇一摇实现的主要代码）
window.addEventListener("devicemotion", function(event) {
   // 处理event.acceleration
   //	x(y,z):设备在x(y,z)方向上的移动加速度值
   //event.accelerationIncludingGravity
   //考虑了重力加速度后设备在x(y,z)
   // event.rotationRate
	//alpha,beta,gamma:设备绕x,y,z轴旋转的角度
  }, true);

