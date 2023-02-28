# Lab 2: Tomáš Hutta 240628

### 2-bit comparator

1. Karnaugh maps for other two functions of 2-bit comparator:

   Greater than:

   ![](https://user-images.githubusercontent.com/124770881/219063410-cbe7ce9a-c6e3-4b85-966b-93325e9a4e6c.png) 
   ![unnamed](https://user-images.githubusercontent.com/124770881/220201896-94805e3d-d893-4f3f-ab8a-cf0ef3bcae93.jpg)


   Less than:

   ![](https://user-images.githubusercontent.com/124770881/219063483-1d17401a-7a75-4a6f-9608-5c12ee9e3619.png)
   ![unnamed (1)](https://user-images.githubusercontent.com/124770881/220201916-4a56d8be-d8fd-4d31-8be6-47de8789e739.jpg)


2. Mark the largest possible implicants in the K-map and according to them, write the equations of simplified SoP (Sum of the Products) form of the "greater than" function and simplified PoS (Product of the Sums) form of the "less than" function.

   ![unnamed (2)](https://user-images.githubusercontent.com/124770881/220201963-2e5b1e57-ae56-42f2-9c2b-59b72d790cc5.jpg)

### 4-bit comparator

1. Listing of VHDL stimulus process from testbench file (`testbench.vhd`) with at least one assert (use BCD codes of your student ID digits as input combinations). Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

   Last two digits of my student ID: **xxxx??**

```vhdl
  begin
    uut_comparator_4bit : entity work.comparator_4bit
        port map(
            a_i           => s_a,
            b_i           => s_b,
            B_greater_A_o => s_B_greater_A,
            B_equals_A_o  => s_B_equals_A,
            B_less_A_o    => s_B_less_A
        );
        p_stimulus : process
    begin
        report "Stimulus process started" severity note;
        s_b <= "1000"; 
        s_a <= "0001";        
        wait for 100 ns;
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A  = '0') and
                (s_B_less_A    = '0'))
        report "Input combination 1000 and 0001 FAILED" severity error;
    
        s_b <= "1000"; 
        s_a <= "0001";        
        wait for 100 ns;
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A  = '0') and
                (s_B_less_A    = '0'))
        report "Input combination 1000 and 0001 FAILED" severity error;
        report "Stimulus process finished" severity note;
        wait;
    end process p_stimulus;
   
```

2. Link to your public EDA Playground example:

   [(https://www.edaplayground.com/x/9Tfg)](https://www.edaplayground.com/x/9Tfg)
