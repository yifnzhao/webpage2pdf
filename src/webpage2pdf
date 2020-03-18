import os
import tempfile
import autopy
import img2pdf


def screenshot(top_left, right_bottom, next_page, total_page):
    rect_size = (right_bottom[0] - top_left[0], right_bottom[1] - top_left[1])
    images = []
    temp_dir = tempfile.mkdtemp()
    for i in range(total_page):
        page_num = "{}".format(i).zfill(len(str(total_page)))
        file_name = os.path.join(temp_dir, 'book-page-{}.png'.format(page_num))
        images.append(file_name)

        autopy.mouse.move(*next_page)
        autopy.mouse.click(delay=1)
        autopy.bitmap.capture_screen((top_left, rect_size)).save(file_name)

    return images


def image2pdf(images):
    with open("book.pdf", "wb") as f:
        f.write(img2pdf.convert(images))


if __name__ == "__main__":
    os.chdir("../data/")
    images = screenshot((134,75), (789,928) , (815,503), 297) # (top left), (bottom right), (loc of next buttom), total page number
    image2pdf(images)
