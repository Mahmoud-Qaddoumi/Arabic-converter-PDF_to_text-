def im_to_text(image_name, out_text="text_out.txt"):  # function to change image to text
    import pytesseract
    from PIL import Image
    outfile = out_text
    f = open(outfile, "a", encoding='utf-8')
    image_data = Image.open(image_name)
    pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
    text = pytesseract.image_to_string(image_data, lang='ara')
    text = str(text)
    text = text.replace('\n', ' ')
    f.write(text)
    f.close()
    return text


def pdf_to_image(pdf_file_name):
    from pdf2image import convert_from_path
    import numpy as np
    import cv2
    import matplotlib.pyplot as plt

    pages = convert_from_path(pdf_file_name, dpi=500)
    image_counter = 1
    for page in pages:
        img = np.array(page)
        file_name = "image_" + str(image_counter) + ".png"
        image_counter = image_counter + 1
        plt.imsave(file_name, img, cmap='gray')

    return image_counter


def show_image(image, title='Image'):
    import matplotlib.pyplot as plt
    plt.imshow(image)
    plt.title(title)
    plt.axis('off')
    plt.show()


img_c = pdf_to_image('test.pdf')
out_f = open("out_text.txt", "a", encoding='utf-8')
end_line = '\n'
dash = "_____________________________________________________________________________________________________________ "

for x in range(3, img_c - 1):
    filename = "image_" + str(x) + ".png"
    text_done = im_to_text(filename)
    z = x - 2
    out_f.write(dash)
    out_f.write(end_line)


out_f.close()
