library IEEE;
use IEEE.std_logic_1164.ALL;

architecture behaviour of main_ytob is
component full_adder_3x is
    Port ( a : in  STD_LOGIC_VECTOR (11 downto 0);
           b : in  STD_LOGIC_VECTOR (11 downto 0);
           s : out  STD_LOGIC_VECTOR (11 downto 0);
           cout : out  STD_LOGIC);
end component;
component shifter_left_2 is 
port ( s_in : in std_logic_vector(11 downto 0);
s_out : out std_logic_vector(11 downto 0)
);
end component; 
component shifter_left_4 is 
port ( s_in : in std_logic_vector(11 downto 0);
s_out : out std_logic_vector(11 downto 0)
);
end component; 
component shift_sright is 
port ( s : in std_logic_vector(2 downto 0);
s_in : in std_logic_vector(11 downto 0);
s_out : out std_logic_vector(11 downto 0)
);
end component; 
component mux_position is
 port ( C0, C1, C2, C3, C4, C5, C6, C7        : in std_logic_vector(11 downto 0);
    Sel                    : in std_logic_vector(2 downto 0);
    center_a                : out std_logic_vector(11 downto 0));
end component;
	signal full_adder_y1, full_adder_y2 : std_logic_vector(11 downto 0);
	signal shift_out4yleft, shift_out2yleft, shifter_rightyout : std_logic_vector(11 downto 0);
	signal hunderd : std_logic_vector(11 downto 0);
	signal C0,C1,C2,C3, C4, C5, C6, C7, center_b        : std_logic_vector(11 downto 0);
	
begin
	C0 <= "000000000000";
	C1 <= "000000000000";
	C2 <= "000000000000";
	C3 <= "000000000000";
	C4 <= "000000000000";
	C5 <= "000000000000";
	C6 <= "000000000000";
	C7 <= "000000000000";
	hunderd <= "000001100100";
	FAy1: full_adder_3x port map(s_in,hunderd,full_adder_y1);
	SL4y: shifter_left_4 port map(full_adder_y1,shift_out4yleft);
	SL2y: shifter_left_2 port map(full_adder_y1,shift_out2yleft);
	FAy2: full_adder_3x port map(shift_out4yleft, shift_out2yleft,full_adder_y2);
	SRy : shift_sright port map(zoom,full_adder_y2,shifter_rightyout); 
	MUXy : mux_position port map(C0, C1, C2, C3, C4, C5, C6, C7, position, center_b); 
	FAy3 : full_adder_3x port map(center_b,shifter_rightyout,b);
end behaviour;

