#pragma once

#include "MSAFluid.h"
//#include "MSATimer.h"
#include "ParticleSystem.h"

#include "ofMain.h"
#include "ofxKinect.h"
#include "ofxOpenCv.h"
#include "ofxOpticalFlowLK.h"


// comment this line out if you don't wanna use TUIO
// you will need ofxTUIO & ofxOsc
//#define USE_TUIO

// comment this line out if you don't wanna use the GUI
// you will need ofxSimpleGuiToo, ofxMSAInteractiveObject & ofxXmlSettings
// if you don't use the GUI, you won't be able to see the fluid parameters
#define USE_GUI


#ifdef USE_TUIO
#include "ofxTuio.h"
#define tuioCursorSpeedMult				0.5	// the iphone screen is so small, easy to rack up huge velocities! need to scale down
#define tuioStationaryForce				0.001f	// force exerted when cursor is stationary
#endif


#ifdef USE_GUI
#include "ofxSimpleGuiToo.h"
#endif

class testApp : public ofBaseApp {
public:
	void setup();
	void update();
	void draw();

	void keyPressed  (int key);
	void mouseMoved(int x, int y );
	void mouseDragged(int x, int y, int button);

	void fadeToColor(float r, float g, float b, float speed);
	void addToFluid(ofVec2f pos, ofVec2f vel, bool addColor, bool addForce);



  float                   colorMult;
  float                   velocityMult;
	int                     fluidCellsX;
	bool                    resizeFluid;
	bool                    drawFluid;
	bool                    drawParticles;

	msa::fluid::Solver      fluidSolver;
	msa::fluid::DrawerGl	fluidDrawer;

	ParticleSystem          particleSystem;

	ofVec2f                 pMouse;



	//kinect stuff

	ofxKinect kinect;

	//openCv Stuff
	ofxCvGrayscaleImage grayImage, bgImage, diffImage; // grayscale depth image
	ofxCvGrayscaleImage grayThreshNear; // the near thresholded image
	ofxCvGrayscaleImage grayThreshFar; // the far thresholded image

	ofxCvContourFinder contourFinder;

	int nearThreshold, farThreshold, repulsForce, repulsRadius;

	vector <ofPolyline> contourPoly;
	vector <ofPath> contour2Draw;

	int simpArg1;
	float simpArg2;
  bool doDrawContour, bDrawGui;
  ofxOpticalFlowLK flow;


#ifdef USE_TUIO
	myTuioClient tuioClient;
#endif

};



