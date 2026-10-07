# AutomationRPAFakturama

RPA script that registers products in an ERP (Fakturama) from an Excel list, the same way a person would do it by hand: by looking at the screen, clicking and typing.

## What it does

Reads `Produtos.xlsx` (one product per row) and, for each product, opens the product form in Fakturama, fills it in, attaches the product picture and saves. It replaces the repetitive part of registering a catalog by hand.

## How it works

1. Opens Fakturama and waits until its logo shows up on the screen.
2. Loads `Produtos.xlsx` with pandas. Columns: ID, Name, Category, GTIN, Supplier, Description, Image, Price, Cost, Stock.
3. For each product: opens New > New product, then fills item number, name, category, GTIN, description, price, cost and stock.
4. Selects the picture from the `Imagens Produtos` folder and saves.

Screen elements are found by image recognition (`pyautogui.locateOnScreen`), using the PNG screenshots in this repository (`logofak.png`, `itemnumber.png`, `price.png` and so on). Three small helpers keep the loop short:

- `encontrar_imagem`: waits until a screenshot appears on screen and returns its position.
- `direita`: gets the point at the right edge of a label, where the input field is.
- `escrever_texto`: pastes text through the clipboard (`pyperclip`), which keeps accents and special characters intact.

`pyautogui.FAILSAFE` is on: move the mouse to a screen corner to stop the script.

## Requirements

- Windows with Fakturama 2 installed. The install path is set in the notebook, so change it if yours is different.
- Python 3 with `pyautogui`, `pandas`, `openpyxl`, `pyperclip`, `opencv-python` and `Pillow`.

## How to run

1. Install the requirements and Fakturama.
2. Take new screenshots of the Fakturama elements and replace the PNG files. Image matching depends on your resolution, scaling and theme, so the provided images may not match your screen.
3. Open `AutomacaoERPs.ipynb` and run the cells. Do not touch the mouse or keyboard while it runs.

## Notes

- This is a practice project, built to learn image-based RPA. The product data and pictures are samples.
- It is slow and fragile by nature: any change in the application layout breaks the matching.
