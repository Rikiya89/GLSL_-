// Example Pixel Shader

// uniform float exampleUniform;

out vec4 fragColor;
void main()
{
	vec3 surfaceNormal = texture(sTD2DInputs[0], vUV.st).rgb;
	vec3 lightDir = vec3(0,-1,0); //light directly down in the y direction
	vec3 refracted = refract(lightDir, surfaceNormal, 1.0 / 1.33); //1.0; index of refraction of air ; 1.33; IoR of water 
	refracted = normalize(refracted);

	//build our intersection plane
	vec3 planeNormal = vec3(0,1,0);//normal points up in the y direction 
	vec3 p0 = vec3(0,-0.5,0);//set the intersection plane a bit below our refractive surface

	//build our ray 
	vec3 ro = vec3(vUV.s,0., vUV.t);
	vec3 rd = refracted;
	

	float t = -dot(ro - p0, planeNormal) / dot(rd, planeNormal);

	//intersect ray with plane 
	vec3 pIntersect = ro + t * rd;
	vec4 color = vec4(pIntersect, 1.0);
	fragColor = TDOutputSwizzle(color);
}
