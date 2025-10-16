/ File Name: AsciiArtGenerator.java

import javax.imageio.ImageIO;
import java.awt.image.BufferedImage;
import java.awt.Color;
import java.io.File;
import java.io.IOException;

public class AsciiArtGenerator {

    public static void main(String[] args) {
        // IMPORTANT: Change this to the path of your image file.
        // The image must be in the same folder as your project.
        String imagePath = "my_photo.png";

        try {
            // Step 1: Read the image file
            File inputFile = new File(imagePath);
            BufferedImage originalImage = ImageIO.read(inputFile);

            // Step 2: Resize the image to a manageable width (e.g., 100 characters)
            int newWidth = 100;
            int newHeight = (int) (originalImage.getHeight() * (double) newWidth / originalImage.getWidth() / 2.5); // Adjust height for character aspect ratio
            BufferedImage resizedImage = new BufferedImage(newWidth, newHeight, BufferedImage.TYPE_INT_RGB);
            resizedImage.getGraphics().drawImage(originalImage, 0, 0, newWidth, newHeight, null);

            // Step 3: Iterate through each pixel of the resized image
            for (int y = 0; y < resizedImage.getHeight(); y++) {
                StringBuilder line = new StringBuilder();
                for (int x = 0; x < resizedImage.getWidth(); x++) {
                    // Get the color of the pixel and convert it to grayscale
                    Color pixelColor = new Color(resizedImage.getRGB(x, y));
                    int brightness = (pixelColor.getRed() + pixelColor.getGreen() + pixelColor.getBlue()) / 3;

                    // Step 4: Map the brightness to an ASCII character
                    line.append(getAsciiChar(brightness));
                }
                System.out.println(line);
            }

        } catch (IOException e) {
            System.out.println("Error: Could not find or read the image file at '" + imagePath + "'.");
            System.out.println("Please make sure the image is in the same folder as the project and the file name is correct.");
        }
    }

    // This method maps a brightness value (0-255) to a character
    private static char getAsciiChar(int brightness) {
        // These characters are ordered from darkest to brightest
        String asciiChars = "$@B%8&WM#*oahkbdpqwmZO0QLCJUYXzcvunxrjft/\\|()1{}[]?-_+~<>i!lI;:,\"^`'. ";
        int index = (brightness * (asciiChars.length() - 1)) / 255;
        return asciiChars.charAt(index);
    }
}
