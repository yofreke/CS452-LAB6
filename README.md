CS452-LAB6
==========
Due Tuesday April 15

There are many ways to create shadows with opengl.  One way is with "shadow mapping."

Shadow mapping with one directional light goes as follows:

- Set up a texture which will hold the depth data from our lights point of view
- Set up a basic MVP matrix which will be used to render the scene from the point of view of the light
- The shaders for rendering here are very simple, since all we have to do is render a black and white texture
- The lighting texture is then used by the main vertex shader and fragment shader.  These shaders use the matricies from earlier to determine where a fragment lies on the lighting texture.
- Anything that is not 'visible' on the lighting textue is considered to be in a shadow, and therefore its color is multiplied by 0.5 (or some other fraction, based on programmers taste)

The technique described above is used for directional lighting, where all light rays are considered to run parallel to one another.  There are also ways of creating other light types, like spot lights and point lights.

A spot light is very similar, but a perspective projection matrix is used instead of an orthographic projection matrix.

A point light is also similar, however instead of one texture for the depth map, a cube map s used.  This means that a texture is rendered so that depth is known from all directions around the point light.