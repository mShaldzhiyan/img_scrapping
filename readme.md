# Part 1

Task: scrape images of cloths and persons wearing cloths, place them in separate folders

Main script: scapper_deep.ipynb

Functions:  

    scrape_images - main function, scraping images from url provided, places them in separate folders. Saves and returns metadata dataframe, which contains cloth title, data-itemid, url for parsing and list of avaliable colors.  
  
    scrape_images_frompos - helper function, accepts dataframe with items metadata and allows to continue image donwloading from selected position in case connection breaks or site prevents connection.  
  
    tile_to_dict - creates dictionary containing item metadata based on tile BeutifulSoup item.  
    save_images - downloads images and places them into folder based on filename (i found out that items that contain 'alternate' in url almost always contain person and items that contain 'lifestyle' in url always contain cloth without person).  
    get_images - downloads all images from cloth item url, if multiple colors is avaliable also downloads them.  
  
Conclusion:  
    I was able to collect ~1500 images of person in clothes and ~400 images of clothes without a person.  
    'no_person' folder consists of images without humans.  
    'person' folder consists of images with humans.  
    Some images without person were placed in person folder, but none of images with person were placed in no_person folder.  
  
Extras:  
    Some pictures i scraped were not images, so i wrote cleaner.ipynb that cleans that up with help of PIL library and places them in 'not_images' folder.  
    I also wrote cleaner_keras.ipynb script, which utilises EfficientNetV2B3 pretrained on imagenet and finetuned on items previously parsed (all no_person items and ~50% of person items which i was sure contained humans) to scan 'person' folder and move suspicious items to folder named 'suspicious'.  

# Part 2

Task: use provided script to create masks of cloth items, create function that given the image of the cloth and the mask of the cloth, outputs the original image of the cloth with the background of the cloth in blue color

Main script: mask.ipynb

Functions:

    preprocess - main function, that given the image of the cloth and the mask of the cloth, outputs the original image of the cloth with the background of the cloth in blue color

    get_mask - function that implements code you provided in google colab, creates a mask image based on provided cloth image

Conclusion:  
    I was able to implement preprocess function with help of open_cv library.