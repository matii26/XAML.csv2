using System;
using System.Collections.Generic;
using System.Windows;
using System.Windows.Controls;

namespace Sudoku
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void CheckButton_Click(object sender, RoutedEventArgs e)
        {
            bool isValid = CheckSudoku();
            if (isValid)
            {
                MessageBox.Show("Gratulacje! Sudoku jest poprawnie uzupełnione.", "Sudoku", MessageBoxButton.OK, MessageBoxImage.Information);
            }
            else
            {
                MessageBox.Show("Niestety, Sudoku jest źle uzupełnione. Spróbuj jeszcze raz.", "Sudoku", MessageBoxButton.OK, MessageBoxImage.Error);
            }
        }

        private bool CheckSudoku()
        {
            // Sprawdzanie poprawności wypełnienia gry Sudoku
            HashSet<string> values = new HashSet<string>();

            foreach (var item in sudokuGrid.Children)
            {
                if (item is Button button && button.Content != null)
                {
                    string content = button.Content.ToString();
                    if (!values.Add(content))
                        return false; // Duplikat
                }
            }

            return true; // Poprawne uzupełnienie
        }

        // Obsługa kliknięcia przycisków 1-16 (Button_Click_1 do Button_Click_16)
        private void Button_Click_1(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_2(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_3(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_4(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_5(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_6(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_7(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_8(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_9(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_10(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_11(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_12(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_13(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_14(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_15(object sender, RoutedEventArgs e) { Button_Click(sender, e); }
        private void Button_Click_16(object sender, RoutedEventArgs e) { Button_Click(sender, e); }

        // Obsługa kliknięcia przycisków
        private void Button_Click(object sender, RoutedEventArgs e)
        {
            Button button = (Button)sender;
            if (button.Content == null)
            {
                button.Content = "1";
            }
            else
            {
                int ile = Int32.Parse(button.Content.ToString());
                if (ile == 4)
                {
                    ile = 1;
                }
                else
                {
                    ile++;
                }
                button.Content = ile.ToString();
            }
        }
    }
}
