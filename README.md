# CS123-FinalProject
A knights quest.
BEGIN CODE FOR BACKGROUND TREES BY DAYTON
float vT=0;
float xT[];
float yT[];
color colorT[];
color colorTt[];
float widthTree[];
float cloudMove=0;
int numTrees;
void setup() {
  size(400, 400);
  numTrees=50;
  xT= new float[numTrees];
  yT= new float[numTrees];
  colorT= new color[numTrees];
  colorTt= new color[numTrees];
  widthTree= new float[numTrees];
  for (int i=0; i<numTrees; i++) {
    xT[i]=random (99*i, 101*i);
    yT[i]=random (50, 80);
    colorT[i]= color(random(135,160),random(80,105),random(35,55));
    colorTt[i]= color(random(0,70),random(180,230),random(100,140));
    widthTree[i]= random(45, 53);
  }
}

void cloud(float cx){
  fill(225,215,225);
  noStroke();
  ellipse(cx+81,73,40,40);
  ellipse(cx+48,82,42,42);
  ellipse(cx+103,117,180,70);
  ellipse(cx+106,82,20,20);
  ellipse(cx+30,100,24,24);
  ellipse(cx+125,80,24,20);
  ellipse(cx+140,77,28,25);
  ellipse(cx+150,83,25,20);
  ellipse(cx+170,95,30,25);
}

void tree(float x, float y, float wT, color cT, color cTt) {
  fill(cT);
  rect(x, y, wT, height-y);
  fill(cTt);
  triangle(x-wT, y, x+2*wT, y, x+wT/2, 2*y-height/2);
}

void draw() {
  smooth();
  background(120, 234, 256);
  cloud(cloudMove);
  pushMatrix();
  translate(-vT, 0);
  for (int i=0; i<numTrees; i++) {
    tree(xT[i], yT[i], widthTree[i], colorT[i], colorTt[i]);
  }
  popMatrix();
  vT+=2;
  fill(40,130,100);
  rect(0, height-70, width, 70);
  cloudMove+=0.2;
}
