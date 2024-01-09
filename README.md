# AutomationRPAFakturama
 The purpose of this automation is simulate an ERP (in this case Fakturama) and insert a list of products in the system. Then you should also download the files in the folder. In these files you have the list of products and images of them. 

 It was used locateOnScreen function of pyautogui in order to locate the images that would trigger that specific event. For locateOnScreen function works in your computer you have to make a screenshot of all png files that you can check in this repository.

 Since the process would repeat a lot it was created functions to save time. 

STEP BY STEP FOR EACH PRODUCT
 1 - open the ERP
 2 - write in all fields information about it product
 3 - insert its image
 4 - save product
