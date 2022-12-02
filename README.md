# Rumeisa-
Steering* FlockingSteering::getSteering()
{
	mLinear = 0;
	mAngular = 0;

   //Gets the align steering result
	mAlign->getSteering();

   //Gets the separate steering result
	mSeparate->getSteering();

   //Gets the cohesion steering result
	mCohesion->getSteering();

   //Combines the three results using a weighted average
   //Weights can be tweaked at runtime
	mLinear = (mAlign->getLinear() * mAlignWeight) + (mSeparate->getLinear() * mSeparationWeight) 
        + (mCohesion->getLinear() * mCohesionWeight);
	mLinear /= mWeightTotal;

	return this;
}
