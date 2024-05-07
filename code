using System;
using System.Collections.Generic;
using System.IO;

namespace ConsoleApp3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            try
            {
                string[] lines = File.ReadAllLines("graph.txt");

                int rowCount = lines.Length;
                int colCount = lines[0].Split(' ').Length;
                int[,] matrix = new int[rowCount, colCount];

                for (int i = 0; i < rowCount; i++)
                {
                    string[] row = lines[i].Split(' ');
                    for (int j = 0; j < colCount; j++)
                    {
                        matrix[i, j] = int.Parse(row[j]);
                    }
                }

                int maxSize = FindLargestSquare(matrix);
                Console.WriteLine("Размер наибольшего квадрата из единиц: " + maxSize);
            }
            catch (Exception ex)
            {
                Console.WriteLine("Ошибка: " + ex.Message);
            }
        }
        static int FindLargestSquare(int[,] matrix)
        {
            int rowCount = matrix.GetLength(0);
            int colCount = matrix.GetLength(1);

            int maxSize = 0;

            int[,] sizes = new int[rowCount, colCount];

            for (int i = 0; i < rowCount; i++)
            {
                sizes[i, 0] = matrix[i, 0];
                if (sizes[i, 0] == 1)
                    maxSize = 1;
            }

            for (int j = 0; j < colCount; j++)
            {
                sizes[0, j] = matrix[0, j];
                if (sizes[0, j] == 1)
                    maxSize = 1;
            }

            for (int i = 1; i < rowCount; i++)
            {
                for (int j = 1; j < colCount; j++)
                {
                    if (matrix[i, j] == 1)
                    {
                        sizes[i, j] = Math.Min(sizes[i - 1, j], Math.Min(sizes[i, j - 1], sizes[i - 1, j - 1])) + 1;
                        maxSize = Math.Max(maxSize, sizes[i, j]);
                    }
                    else
                    {
                        sizes[i, j] = 0;
                    }
                }
            }

            return maxSize;
        }
    }
}
