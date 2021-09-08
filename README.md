--Codigo creado para asigarle un valor a los segmentos y encenderlos divididos entre decenas y unidades
--segun el resultado de la operacion

LIBRARY IEEE;
USE ieee.std_logic_1164.all;
--------------------------------------------------
ENTITY display IS
 PORT(    disdec : OUT STD_LOGIC_VECTOR(6 DOWNTO 0);--Bits para encender los segmentos del numero resultante en las decenas
          unidad : IN  STD_LOGIC_VECTOR(3 DOWNTO 0);--Parte de las unidades
          disuni : OUT STD_LOGIC_VECTOR(6 DOWNTO 0);--Bits para encender los segmentos del numero resultante en las unidades 	
	   out_decena : IN  STD_LOGIC_VECTOR(3 DOWNTO 0));--Parte de las decenas despues de analizar el negativo
END ENTITY display;
--------------------------------------------------
ARCHITECTURE operation OF display IS
BEGIN
	 
	 with out_decena select--Se realiza un with select teniendo en cuenta el out_decena 
	disdec <=--Dependiendo de este se le asigna un valor al disdec para encender los segmentos y formar numeros del 0 al 9
	 "1000000" WHEN  "0000",
	 "1111001" WHEN  "0001",
	 "0100100" WHEN  "0010",
	 "0110000" WHEN  "0011",
	 "0011001" WHEN  "0100",
	 "0010010" WHEN  "0101",
	 "0000010" WHEN  "0110",
	 "1111000" WHEN  "0111",
	 "0000000" WHEN  "1000",
	 "0011000" WHEN  "1001",
	 "0111111" WHEN  "1111",--Caso para encender el menos
	 "0000110" WHEN  OTHERS;
	 
	 with  unidad select--Se realiza un with select teniendo en cuenta el unidad
	 disuni<=--Dependiendo de este se le asigna un valor al disuni para encender los segmentos y formar numeros del 0 al 9
	 "1000000" WHEN  "0000",
	 "1111001" WHEN  "0001",
	 "0100100" WHEN  "0010",
	 "0110000" WHEN  "0011",
	 "0011001" WHEN  "0100",
	 "0010010" WHEN  "0101",
	 "0000010" WHEN  "0110",
	 "1111000" WHEN  "0111",
	 "0000000" WHEN  "1000",
	 "0011000" WHEN  "1001",
	 "0000110" WHEN  OTHERS;
	 
END ARCHITECTURE operation;
