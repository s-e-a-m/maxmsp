# maxmsp
Esempio di scrittura per funzioni.

```
calc (delay, time)
{
	History direction(-1);	
	History ramp(0);
	History del1(0);
	History del2(0);
	 
	test1 = ((ramp == 0) && (del1 != delay));
	test2 = ((ramp == 1) && (del2 != delay));
	
	del2 = test1 ? delay : del2;
	del1 = test2 ? delay : del1;
	
	sampletime = 1 / (samplerate * time / 1000);
	direction = (test1 || test2) ? -direction : direction;
	ramp = clip(ramp + (direction * sampletime), 0, 1);
	
	return ramp, del1, del2;
}

Param ramptime(75);

out1, out2, out3 = calc(in1, ramptime);
