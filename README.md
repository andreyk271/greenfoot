# greenfoot
public class Crab extends Actor
{
    

    /**
     * Move forward in the current direction.
     */
    public void act()
    {
        if (Greenfoot.isKeyDown("up"))
        {move (1);}
        if (Greenfoot.isKeyDown("down"))
        {move (-1);}
        if (Greenfoot.isKeyDown("left"))
        {turn (-90);
        move (1);}
        if (Greenfoot.isKeyDown("right"))
        {turn (90);
        move (1);}
        Actor Wombat = getOneObjectAtOffset(0, 0, Wombat.class);
        if(Wombat !=null) {
            getWorld().removeObject(Wombat);
            Greenfoot.playSound("pop.wav");
            totalCount = totalCount + 1;
        }
    }
}

public class Counter extends Actor
{
    private int totalCount = 0;

    /**
     * A constructor for the counter, which sets the counter's initial text image
     */
    public Counter()
    {
        setImage(new GreenfootImage("Wombats Eatern: " +totalCount, 20, Color.WHITE, Color.BLACK));
    }

    /**
     * Increase the total amount displayed on the counter, by a given amount.
     */
    public void bumpCount(int amount)
    {
        totalCount += amount;
        setImage(new GreenfootImage("Wombats Eatern: " +totalCount, 20, Color.WHITE, Color.BLACK));
    }
}

public class theWombat extends Actor
{
    

    /**
     * Move forward in the current direction.
     */
    public void move()
    {
        move(Greenfoot.getRandomNumber(2));
        turn(Greenfoot.getRandomNumber(90));
    }

    
    
    /**
     *
     */
    public void checkForWombat()
    {
        Actor theWombat = getOneObjectAtOffset(0, 0, Wombat.class);
        if (theWombat != null)
        {
            WombatWorld EatingWorld = (WombatWorld) getWorld();
            eatingWorld.removeObject(theWombat);
            Greefoot.playSound("pop.wav");
            bumpCounter(1);
        }
    }

    
    /**
     * A method that accesses the world's counter and bumps it by a specified integer.
     */
    public void bumbpCounter(int bumpAmount)
    {
        WombatWorld counterWorld = (wombatWorld) getWorld();
        Counter theCounter = counterWorld.getCounter();
        theCounter.bumpCount(bumpAmount);
    }
}
