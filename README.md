# SDL-DREAMHAL Version 1.0 based on SDL1.2.13
# DREAMCAST hardware +opengl SDL FAST BLIT SPEED CUSTOM
Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer.
Credit Chui for doing all this work so i could upgrade it and improve it for the new GLDC and Dreamhal math routines and functions 
# Old version
http://chui.dcemu.co.uk/sdl.html
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
 Before SDL_Init call, you can choose SDL video driver for Dreamcast. The following values are valid.

- SDL_DC_DMA_VIDEO (default)
	Use DMA video drive. It is the fastest video driver using double buffer since every graphic access uses RAM and SDL_Flip function sends data to VRAM using DMA.
------------------------------------------------------------------------------------------------------
- SDL_DC_TEXTURED_VIDEO
	Use Textured video driver. If you want to use a virtual resolution (no 640x480, 320x240, ... ), you can use this driver for scaling using hardware texture. PVR textures is always 2^n (128x128, 256x128, 512x256, ... ) and these resolutions are real SDL_Surface resolutions.
Using SDL_FULLSCREEN flag only 2^n resolution are allowed, but if you do not use this flag it will be automatically fit to SDL_SetVideoMode resolution. See SDL_DC_SetWindow for manual fit.
----------------------------------------------------------------------------------------------
- SDL_DC_DIRECT_VIDEO
- ----------------------------
	Use Direct buffer video driver. Maybe faster than DMA driver if you do not use double buffer.
	
	
	SDL_DC_SetWindow(int width, int height)
	Only for textured video driver and must be called after SDL_SetVideoMode, this function allow setting the visible area (hardware scaled). If you open a 512x256 texture resolution, only smaller virtual resolution is allowed.
	-------------------------------------------------------------------------------------------------
	
SDL_DC_VerticalWait(SDL_bool value)
-------------------------------------------------
Enable/disable wait for vertical retrace before blitting to PVR hardware.		
	
SDL_DC_ShowAskHz(SDL_bool value)
------------------------------------
Enable/disable ask for 50/60Hz (only for PAL Dreamcasts) video.		
	
SDL_DC_Default60Hz(SDL_bool value)
--------------------------------------
True for 60Hz default display (only for PAL Dreamcasts).

# SDL_DC_MapKey(int joy, SDL_DC_button button, SDLKey key)

Map a Dreamcast button to SDLKey. First parameter is number of Dreamcast joystick port (0,1,2 or 3). The following table shows valid values for second parameter and default values for third parameter.
- Value	          Port 0	 Port 1 Port 2 Port 3
- 
----------------------------------------------------------
- SDL_DC_START	SDLK_RETURN	SDLK_z	SDLK_v	SDLK_m
- SDL_DC_A	SDLK_LCTRL	SDLK_e	SDLK_y	SDLK_o
SDL_DC_B	SDLK_LALT	SDLK_q	SDLK_r	SDLK_u
SDL_DC_X	SDLK_SPACE	SDLK_x	SDLK_b	SDLK_COMMA
SDL_DC_Y	SDLK_LSHIFT	SDLK_c	SDLK_n	SDLK_PERIOD
SDL_DC_L	SDLK_TAB	SDLK_1	SDLK_4	SDLK_8
SDL_DC_R	SDLK_BACKSPACE	SDLK_2	SDLK_5	SDLK_9
SDL_DC_LEFT	SDLK_LEFT	SDLK_a	SDLK_f	SDLK_j
SDL_DC_RIGHT	SDLK_RIGHT	SDLK_d	SDLK_h	SDLK_l
SDL_DC_UP	SDLK_UP	SDLK_w	SDLK_t	SDLK_i
SDL_DC_DOWN	SDLK_DOWN	SDLK_s	SDLK_g	SDLK_k``
------------------------------------------------------------
