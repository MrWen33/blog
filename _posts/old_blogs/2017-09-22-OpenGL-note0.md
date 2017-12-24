---
layout: post
title: OpenGL学习日志（0）
tags: [OpenGL]
---

glutInit(&argc, argv);//初始化glut

　　glutInitDisplayMode(unsigned int displaymode);//设置显示模式

　　glutInitWindowSize(int width,int height);//设置窗口大小

　　glewInit();//初始化glew

　　glutMainLoop();//进入opengl消息循环

　　typedef float M3DMatrix44f[16];

　　typedef double M3DMatrix44d[16];

　　glEnable(GLenum cap);//打开某opengl模式

　　glDisable(GLenum cap);//关闭某opengl模式

　　glBegin(GLenum mode);

　　glEnd()

　　在glBegin与glEnd函数间可以调用绘图函数：



GLFrustum类：设置投影矩阵：

　　void GLFrustum::SetOrthographic(GLfloat xMin, GLfloat xMax, GLfloat yMin, GLfloat yMax, GLfloat zMin, GLfloat zMax);

　　　　设置正投影矩阵，参数指定视景体的范围

　　void GLFrustum::SetPerspective(float fFov, float fAspect, float fNear, float fFar);

　　　　设置透视投影矩阵，参数分别为垂直方向上的视场角度，窗口宽度与高度的纵横比，到近裁剪面与远裁剪面的距离

