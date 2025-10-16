package com.example.demo;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class QuadraticEquationTest {
    private static final double EPSILON = 1e-10;
    
    @Test
    public void testNoRealRoots() {
        QuadraticEquation solver = new QuadraticEquation();
        double[] roots = solver.solve(1, 0, 1);
        assertEquals(0, roots.length);
    }
    
    @Test
    public void testTwoDistinctRoots() {
        QuadraticEquation solver = new QuadraticEquation();
        double[] roots = solver.solve(1, 0, -1);
        
        assertEquals(2, roots.length);
        assertArrayEquals(new double[]{1, -1}, roots, EPSILON);
    }
    
    @Test
    public void testSingleRootMultiplicityTwo() {
        QuadraticEquation solver = new QuadraticEquation();
        double[] roots = solver.solve(1, 2, 1);
        
        assertEquals(1, roots.length);
        assertEquals(-1, roots[0], EPSILON);
    }
    
    @Test
    public void testCoefficientAZeroThrowsException() {
        QuadraticEquation solver = new QuadraticEquation();
        
        assertThrows(IllegalArgumentException.class, () -> {
            solver.solve(0, 1, 1);
        });
    }
    
    @Test
    public void testSmallDiscriminant() {
        QuadraticEquation solver = new QuadraticEquation();
        
        // Случай с очень малым дискриминантом
        double[] roots = solver.solve(1, 2, 1 + 1e-15);
        assertEquals(1, roots.length);
    }
    
    @Test
    public void testSpecialDoubleValues() {
        QuadraticEquation solver = new QuadraticEquation();
        
        assertThrows(IllegalArgumentException.class, () -> {
            solver.solve(Double.NaN, 1, 1);
        });
        
        assertThrows(IllegalArgumentException.class, () -> {
            solver.solve(Double.POSITIVE_INFINITY, 1, 1);
        });
    }
    
    @Test
    public void testVerySmallDiscriminantCases() {
        QuadraticEquation solver = new QuadraticEquation();
        
        // Положительный дискриминант (но очень малый)
        double[] twoRoots = solver.solve(1, 2, 1 + 1e-12);
        assertEquals(2, twoRoots.length);
        
        // Отрицательный дискриминант (но очень малый)
        double[] noRoots = solver.solve(1, 2, 1 + 1e-8);
        assertEquals(0, noRoots.length);
    }
}
