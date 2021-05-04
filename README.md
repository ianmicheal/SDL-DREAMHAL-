# SDL-DREAMHAL Version 1.0 based on SDL1.2.13
DREAMCAST hardware +opengl SDL FAST BLIT SPEED CUSTOM
Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer.	
  UPGRADED blitspeed using moops dreamhal sh4 asm memcpy and memset bult in.
	BASED on Chui's SDL port for Dreamcast is a SDL (v1.2.9) driver and it is based on Bero's driver, but it has new features as addons:	
	Fast DMA video driver.
	Textured video driver for virtual resolutions.
	Direct framebuffer video driver using store queues.
	Correct OpenGL integration.
	Fast threaded audio driver.
	Mouse emulation using analog pad.
	Mapped keys as pad buttons.
	Correct timer driver.
 Now using GLDC  https://gitlab.com/simulant/GLdc
	OpenGL (Open Graphics Library) is a standard specification defining a cross-language cross-platform API for writing applications that produce 2D and 3D computer graphics. The    interface consists of over 250 different function calls which can be used to draw complex three-dimensional scenes from simple primitives.	
	Kazade's Dreamcast OpenGL is a more compatible OpenGL (v1.2) library GLDC:	
	Full KallistiOS and SDL integration.
	Texture color and size conversions.
	Two texture internal color mode supported: RGB5551 and RGB4444.
	Fast primitive list render.
	
	----------------------------------------------------------------------------------
	- VIDEO
	- Before SDL_Init call, you can choose SDL video driver for Dreamcast. The following values are valid.

- SDL_DC_DMA_VIDEO (default)
	Use DMA video drive. It is the fastest video driver using double buffer since every graphic access uses RAM and SDL_Flip function sends data to VRAM using DMA.

- SDL_DC_TEXTURED_VIDEO
	Use Textured video driver. If you want to use a virtual resolution (no 640x480, 320x240, ... ), you can use this driver for scaling using hardware texture. PVR textures is always 2^n (128x128, 256x128, 512x256, ... ) and these resolutions are real SDL_Surface resolutions.
Using SDL_FULLSCREEN flag only 2^n resolution are allowed, but if you do not use this flag it will be automatically fit to SDL_SetVideoMode resolution. See SDL_DC_SetWindow for manual fit.

- SDL_DC_DIRECT_VIDEO
	Use Direct buffer video driver. Maybe faster than DMA driver if you do not use double buffer.
	
	
	SDL_DC_SetWindow(int width, int height)
	Only for textured video driver and must be called after SDL_SetVideoMode, this function allow setting the visible area (hardware scaled). If you open a 512x256 texture resolution, only smaller virtual resolution is allowed.
