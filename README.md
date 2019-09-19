# samplewebpage
Sample Web Page
var RADIUS = 100;
var OFF_SCREEN = -200;
var DELAY = 1000;
var ball;


function start()
{
	setupBall();
	setTimer(changeBall, DELAY);
	mouseClickMethod(kill);
}


function changeBall()
{
	var x = Randomizer.nextInt(ball.getRadius(),
		getWidth() - ball.getRadius());
	var y = Randomizer.nextInt(ball.getRadius(), getHeight() - ball.getRadius());
	
	ball.setPosition(x, y);
	changeColor();
}


function changeColor()
{
	var colorCode = Randomizer.nextInt(0, 2);
	var color;
	
	if(colorCode == 0)
	{
		color = Color.red;
	}
	else if(colorCode == 1)
	{
		color = Color.yellow;
	}
	else
	{
		color = Color.green;
	}
	
	ball.setColor(color);
}

function setupBall()
{
	ball = new Circle(RADIUS);
	ball.setPosition(OFF_SCREEN, OFF_SCREEN);
	add(ball);
}

function kill(e)
{
    var elem = getElementAt(e.getX(),e.getY);
    if(elem != null)
    {
        ball.setColor(Color.black);
    }
}
