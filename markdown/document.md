
---

#### 000

@@@
{
    "title": "arctangent demo",
    "author": "doxas",
    "description": "arctangent distorsion."
}
@@@

---

|||
precision mediump float;
uniform vec2  resolution;
uniform vec2  mouse;
uniform float time;
uniform sampler2D backbuffer;

const vec3 pinkColor = vec3(1.0, 0.1, 0.5);
const vec3 blueColor = vec3(0.1, 0.3, 0.9);

float waveNeon(vec2 p, float power, float width, float height, float speed){
    float x = cos(abs(p.x * width));
    float y = power / abs(p.y + sin(p.x * 25.0 + time * speed) * height);
    return max(x * y, 0.0);
}

void main(){
    vec2 p = (gl_FragCoord.xy * 2.0 - resolution) / min(resolution.x, resolution.y);
    vec2 m = mouse * 2.0 - 1.0;
    float t = min(time, 2.0) * 0.5;
    p = p * abs(atan(p.y / p.x));
    float a = waveNeon(p, 0.2, 5.0, 0.25 + abs(m.x), 0.75);
    float b = waveNeon(p, 0.5, 2.5, 0.5  + abs(m.y), 0.25);
    gl_FragColor = vec4((pinkColor * a + blueColor * b) * t, 1.0);
}
|||

---

#### 000

@@@
{
    "title": "glslsandbox default",
    "author": "mr.doob",
    "description": "in the page of new shader."
}
@@@

---

|||
#ifdef GL_ES
precision mediump float;
#endif

#extension GL_OES_standard_derivatives : enable

uniform float time;
uniform vec2 mouse;
uniform vec2 resolution;

void main( void ) {

	vec2 position = ( gl_FragCoord.xy / resolution.xy ) + mouse / 4.0;

	float color = 0.0;
	color += sin( position.x * cos( time / 15.0 ) * 80.0 ) + cos( position.y * cos( time / 15.0 ) * 10.0 );
	color += sin( position.y * sin( time / 10.0 ) * 40.0 ) + cos( position.x * sin( time / 25.0 ) * 40.0 );
	color += sin( position.x * sin( time / 5.0 ) * 10.0 ) + sin( position.y * sin( time / 35.0 ) * 80.0 );
	color *= sin( time / 10.0 ) * 0.5;

	gl_FragColor = vec4( vec3( color, color * 0.5, sin( color + time / 3.0 ) * 0.75 ), 1.0 );

}
|||

---

---

## enjoy shader life

---

## enjoy shader life

### thank you!!

---


