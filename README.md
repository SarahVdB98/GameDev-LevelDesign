# GameDev-LevelDesign

Om een level te maken hebben we in de level klasse een 2D array aangemaakt van bytes (0-255):
  
  ´´´
  public byte[,] tileArray = new Byte[,]
        {
            {0,0,0,0,0,0 },
            {0,0,0,0,0,0 },
            {1,0,1,0,1,0 },
            {0,1,0,1,0,1 },
        };
 
 ´´´
 
 Deze array bevat getallen, en deze getallen representeren level elementen zoals blokjes, bomen, ... In bovenstaand voorbeeld bevat het een 0 voor niets, en een 1 voor een blokje.
 Wanneer een level wordt aangemaakt roep ik de CreateWorld methode op:
 
 ´´´
 public void CreateWorld()
        {
            for (int x = 0; x < 4; x++)
            {
                for (int y = 0; y < 6; y++)
                {
                    if (tileArray[x, y] == 1)
                    {
                        blokArray[x, y] = new Blok(texture, new Vector2(y * 128, x * 64));
                    }
                }
            }
        }
 ´´´
 
 Deze methode itereert over de 2D array en converteert de bytearray naar een array van blokken (level elementen). (PS: werk hier met abstractie!)
 
 Daarna maken we een draw methode aan die we vanuit de game klasse aanroepen om elk frame het level te tekenen:
 
 ´´´
 
   public void DrawWorld(SpriteBatch spritebatch)
        {
            for (int x = 0; x < 4; x++)
            {
                for (int y = 0; y < 6; y++)
                {
                    if (blokArray[x, y] != null)
                    {
                        blokArray[x, y].Draw(spritebatch);
                    }
                }
            }

        }
        
 ´´´
 
