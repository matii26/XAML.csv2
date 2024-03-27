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


<Window x:Class="Sudoku.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Sudoku" Height="450" Width="800">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="*" />
            <RowDefinition Height="Auto" />
        </Grid.RowDefinitions>
        <TabControl>
            <TabItem Header="4x4">
                <UniformGrid Name="sudokuGrid" Columns="4">
                    <Button Click="Button_Click_1"/>
                    <Button Click="Button_Click_2"/>
                    <Button Click="Button_Click_3"/>
                    <Button Click="Button_Click_4"/>
                    <Button Click="Button_Click_5"/>
                    <Button Click="Button_Click_6"/>
                    <Button Click="Button_Click_7"/>
                    <Button Click="Button_Click_8"/>
                    <Button Click="Button_Click_9"/>
                    <Button Click="Button_Click_10"/>
                    <Button Click="Button_Click_11"/>
                    <Button Click="Button_Click_12"/>
                    <Button Click="Button_Click_13"/>
                    <Button Click="Button_Click_14"/>
                    <Button Click="Button_Click_15"/>
                    <Button Click="Button_Click_16"/>
                </UniformGrid>
            </TabItem>
        </TabControl>
        <Button Grid.Row="1" Width="100" Height="50" Content="Sprawdź" Click="CheckButton_Click"/>
    </Grid>
</Window>



private void Button_Click_16(object sender, RoutedEventArgs e)
{
    bool isValid = CheckSudoku(); // Wywołanie funkcji sprawdzającej poprawność gry Sudoku
    if (isValid)
    {
        // Wyświetlenie okienka informacyjnego o poprawnym uzupełnieniu Sudoku
        MessageBox.Show("Gratulacje! Sudoku jest poprawnie uzupełnione.", "Sudoku", MessageBoxButton.OK, MessageBoxImage.Information);
    }
    else
    {
        // Wyświetlenie okienka ostrzegawczego o błędnym uzupełnieniu Sudoku
        MessageBox.Show("Niestety, Sudoku jest źle uzupełnione. Spróbuj jeszcze raz.", "Sudoku", MessageBoxButton.OK, MessageBoxImage.Error);
    }
}

// Funkcja sprawdzająca poprawność wypełnienia gry Sudoku
private bool CheckSudoku()
{
    // Tutaj znajduje się logika sprawdzająca poprawność gry Sudoku
    // Należy zaimplementować odpowiednią logikę, która sprawdzi, czy gra Sudoku jest poprawnie uzupełniona
    // Funkcja powinna zwrócić true, jeśli Sudoku jest poprawnie uzupełnione, w przeciwnym razie zwrócić false
    // Poniżej znajduje się przykładowa implementacja

    // Przykładowa implementacja - zawsze zwraca false (do zastąpienia własną implementacją)
    return false;
}



private bool CheckSudoku()
{
    // Sprawdzanie poprawności wierszy
    for (int row = 0; row < 4; row++)
    {
        HashSet<string> rowValues = new HashSet<string>();
        for (int col = 0; col < 4; col++)
        {
            Button button = GetButtonAt(row, col);
            if (button.Content == null)
                return false; // Gra nie jest kompletna

            string content = button.Content.ToString();
            if (!rowValues.Add(content))
                return false; // Duplikat w wierszu
        }
    }

    // Sprawdzanie poprawności kolumn
    for (int col = 0; col < 4; col++)
    {
        HashSet<string> colValues = new HashSet<string>();
        for (int row = 0; row < 4; row++)
        {
            Button button = GetButtonAt(row, col);
            string content = button.Content.ToString();
            if (!colValues.Add(content))
                return false; // Duplikat w kolumnie
        }
    }

    // Sprawdzanie poprawności małych kwadratów 2x2
    for (int startRow = 0; startRow < 4; startRow += 2)
    {
        for (int startCol = 0; startCol < 4; startCol += 2)
        {
            HashSet<string> squareValues = new HashSet<string>();
            for (int row = startRow; row < startRow + 2; row++)
            {
                for (int col = startCol; col < startCol + 2; col++)
                {
                    Button button = GetButtonAt(row, col);
                    string content = button.Content.ToString();
                    if (!squareValues.Add(content))
                        return false; // Duplikat w małym kwadracie 2x2
                }
            }
        }
    }

    return true; // Wszystkie warunki są spełnione - Sudoku jest poprawnie uzupełnione
}

private Button GetButtonAt(int row, int col)
{
    // Pobieranie przycisku na podstawie współrzędnych w siatce 4x4
    foreach (var child in sudokuGrid.Children)
    {
        if (child is UniformGrid grid && Grid.GetRow(grid) == row && Grid.GetColumn(grid) == col)
        {
            foreach (var button in grid.Children)
            {
                if (button is Button)
                {
                    return (Button)button;
                }
            }
        }
    }
    return null;
}
