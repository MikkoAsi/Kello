import pygame
import math
from datetime import datetime

pygame.init()
leveys, korkeus = 640, 480
red = (255, 0, 0)
blue = (0, 0, 255)
white = (255,255,255)
black = ((0,0,0))
grey = (97,97,97)
orange = (255,128,0)

naytto = pygame.display.set_mode((leveys, korkeus))
kello = pygame.time.Clock()

def koordinaatit(kulma, pituus):
    x = 320+math.cos(kulma) * pituus 
    y = 240+math.sin(kulma) * pituus
    return x, y

while True:
    for tapahtuma in pygame.event.get():
        if tapahtuma.type == pygame.QUIT:
            exit()        
        
    naytto.fill(black)

    time = datetime.now()
    sekuntti = time.second
    minuutti = time.minute
    tunti = time.hour
    pvm = time.strftime("%d.%m")
    pygame.display.set_caption(time.strftime("%H:%M:%S"))   

    pygame.draw.circle(naytto, orange, (320, 240), 210)       
    pygame.draw.circle(naytto, white, (320, 240), 200)                    

    for i in range(1,61):
        kulma = (i-15)*2*math.pi/60
        pygame.draw.line(naytto, black, (320, 240), koordinaatit(kulma, 185), 3)
        pygame.draw.line(naytto, white, (320, 240), koordinaatit(kulma, 175), 5)

    for i in range(1,13):
        kulma = (i-3)*2*math.pi/12
        pygame.draw.line(naytto, black, (320, 240), koordinaatit(kulma, 185), 6)
        pygame.draw.line(naytto, white, (320, 240), koordinaatit(kulma, 160), 8)

    kulma_s = (sekuntti-15)*2*math.pi/60
    pygame.draw.line(naytto, red, (320, 240), koordinaatit(kulma_s, 180), 2)
    
    kulma_m = (minuutti-15)*2*math.pi/60 + ((sekuntti)*2*math.pi/60)/60
    pygame.draw.line(naytto, black, (320, 240), koordinaatit(kulma_m, 170), 4)
    
    if 0 <= tunti <= 12:
        kulma_h = (tunti-3)*2*math.pi/12 + ((minuutti)*2*math.pi/60)/12 + ((sekuntti)*2*math.pi/60)/60/12
    elif 13 <= tunti <= 24:
        kulma_h = (tunti-15)*2*math.pi/12 + ((minuutti)*2*math.pi/60)/12 + ((sekuntti)*2*math.pi/60)/60/12
    pygame.draw.line(naytto, black, (320, 240), koordinaatit(kulma_h, 140), 6)

    fontti = pygame.font.SysFont("Calibri", 20, True)
    teksti = fontti.render(pvm, True, black)
    naytto.blit(teksti,(375,280))

    pygame.display.flip()
    kello.tick(60)
