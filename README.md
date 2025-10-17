Najpierw po wybraniu odpowieniego kotrolera z listy i storzeniu projektu ustawiłem pin PA% na GPIO_Output i zmieniłem jego nazwęna DIODA
Nstępnie ustawiłem "clock source" dla timeraa TIM2 na "internl clock", włączyłem global interrupt, prescaler ustawiłem na 59999 i counter period na 999, ponieważ jeśli dobrze rozumiem to będzie się on przerywał co 0,1 sekund co przełoży się na 5Hz częstotliwości mrugania diody
W RCC wybrałem "BYPASS Clock Sorce", ponieważ z tego co rozumiem to umożliwa mi to póżniej w zakładce clock configoration ustawić częstotliwość wejścia na 16MHz
Włączyłem IWDG, z tego co rozumiem to od WWDG różni siętym że ma swój zewnętrzny zegar oraz że jest wystarczjący do prostych programów, counter clock prescaler ustawiłem na 32 a down-counter reload value na 3750 ny się resetował co około 1 sekundę

W clock Configuration ustawiłem input frequency na 16 MHz a PLL source Mux na HSE
System Clock Mux ustawiłem na PLLCLK i SYSCLK na 120Mhx (i tu nie wiem czy to jest poprawnie, w jednym z poradników, prowadzący powiedział aby ustaawić to na maks by było płynniej)

We funkcji main rzed while(1) wystartowałem timer z przerywaniem
w nieskończonej pętli jest odświeżanie watchdoga
A w USER CODE 4 callbeck, który wywołuje się przy przepełnieniu timer 

Nie mam jak przetestować tego programu więc nie mam pojęcia czy wszystko działa, ale jeśli dobrze zinterpretowałem informacje z poradników i forum to powinno działać
