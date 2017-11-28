/**
 * A class that runs implements several simple transformations on 2D image arrays.
 * <p>
 * This file contains stub code for your image transformation methods that are called by the main
 * class. You will do your work for this MP in this file.
 * <p>
 * Note that you can make several assumptions about the images passed to your functions, both by the
 * web front end and by our testing harness:
 * <ul>
 * <li>You will not be passed empty images.</li>
 * <li>All images will have even width and height.</li>
 * </ul>
 *
 * @see <a href="https://cs125.cs.illinois.edu/MP/4/">MP4 Documentation</a>
 */
public class Transform {

    /**
     * Default amount to shift an image's position. Not used by the testing suite, so feel free to
     * change this value.
     */
    public static final int DEFAULT_POSITION_SHIFT = 16;
    /**
     * Maximum value of color.
     */
    public static final int MAX_COLOR = 255;
    /**
     * Location of first bit of green color.
     */
    public static final int GREEN_CHANNEL = 8;
    /**
     * Location of first bit of blue color.
     */
    public static final int BLUE_CHANNEL = 16;
    /**
     * Location of first bit of alpha.
     */
    public static final int ALPHA_CHANNEL = 24;
    /**
     * Location of byte for red.
     */
    public static final int RED_BYTE = 0;
    /**
     * Location of byte for green.
     */
    public static final int GREEN_BYTE = 1;
    /**
     * Location of byte for blue.
     */
    public static final int BLUE_BYTE = 2;
    /**
     * Location of byte for alpha.
     */
    public static final int ALPHA_BYTE = 3;
    /**
     * Total bytes in a color.
     */
    public static final int TOTAL_BYTES = 4;

    /**
     * Pixel value to use as filler when you don't have any valid data. All white with complete
     * transparency. DO NOT CHANGE THIS VALUE: the testing suite relies on it.
     */
    public static final int FILL_VALUE = 0x00FFFFFF;

    /**
     * Shift the image left by the specified amount.
     * <p>
     * Any pixels shifted in from off screen should be filled with FILL_VALUE. This function <i>does
     * not modify the original image</i>.
     *
     * @param originalImage the image to shift to the left
     * @param amount the amount to shift the image to the left
     * @return the shifted image
     */
    public static int[][] shiftLeft(final int[][] originalImage, final int amount) {
        int shiftAmount = 0;
        if (amount > originalImage.length) {
            shiftAmount = originalImage.length;
        } else {
            shiftAmount = amount;
        }
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < originalImage.length - shiftAmount; row++) {
            for (int column = 0; column < originalImage[0].length; column++) {
                newImage[row][column] = originalImage[row + shiftAmount][column];
            }
        }
        for (int row = originalImage.length - shiftAmount; row < originalImage.length; row++) {
            for (int column = 0; column < originalImage[0].length; column++) {
                newImage[row][column] = FILL_VALUE;
            }
        }
        return newImage;
    }

    /*
     * Shift right like above.
     */
    /**
     *
     * @param originalImage original Image.
     * @param amount amount to be shifted right.
     * @return shifted picture.
     */
    public static int[][] shiftRight(final int[][] originalImage, final int amount) {
        int shiftAmount = 0;
        if (amount > originalImage.length) {
            shiftAmount = originalImage.length;
        } else {
            shiftAmount = amount;
        }
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = newImage.length - 1; row > shiftAmount - 1; row--) {
            for (int column = 0; column < originalImage[0].length; column++) {
                newImage[row][column] = originalImage[row - shiftAmount][column];
            }
        }
        for (int row = shiftAmount - 1; row > -1; row--) {
            for (int column = 0; column < originalImage[0].length; column++) {
                newImage[row][column] = FILL_VALUE;
            }
        }
        return newImage;
    }

    /**
     * Shift up like above.
     */
    /**
     *
     * @param originalImage original Image.
     * @param amount amount to be shifted up.
     * @return shifted picture.
     */
    public static int[][] shiftUp(final int[][] originalImage, final int amount) {
        int shiftAmount = 0;
        if (amount > originalImage[0].length) {
            shiftAmount = originalImage[0].length;
        } else {
            shiftAmount = amount;
        }
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = 0; column < originalImage[0].length - shiftAmount; column++) {
                newImage[row][column] = originalImage[row][column + shiftAmount];
            }
        }
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = originalImage[0].length - shiftAmount;
                    column < originalImage[0].length; column++) {
                newImage[row][column] = FILL_VALUE;
            }
        }
        return newImage;
    }

    /**
     * Shift down like above.
     */
    /**
     *
     * @param originalImage original Image.
     * @param amount amount to be shifted down.
     * @return shifted picture.
     */
    public static int[][] shiftDown(final int[][] originalImage, final int amount) {
        int shiftAmount = 0;
        if (amount > originalImage[0].length) {
            shiftAmount = originalImage[0].length;
        } else {
            shiftAmount = amount;
        }
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = originalImage[0].length - 1; column > shiftAmount - 1; column--) {
                newImage[row][column] = originalImage[row][column - shiftAmount];
            }
        }
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = shiftAmount - 1; column > -1; column--) {
                newImage[row][column] = FILL_VALUE;
            }
        }
        return newImage;
    }
    /**
     * Rotate the image left by 90 degrees around its center.
     * <p>
     * Any pixels rotated in from off screen should be filled with FILL_VALUE. This function <i>does
     * not modify the original image</i>.
     *
     * @param originalImage the image to rotate left 90 degrees
     * @return the rotated image
     */
    public static int[][] rotateLeft(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = FILL_VALUE;
            }
        }
        int[][] square = cropSquare(originalImage);
        int[][] rotatedsquare = rotateRightSquare(square);
        rotatedsquare = rotateRightSquare(rotatedsquare);
        rotatedsquare = rotateRightSquare(rotatedsquare);
        if (rotatedsquare.length == originalImage.length) {
            int sideLength = (originalImage[0].length - originalImage.length) / 2;
            for (int row = 0; row < newImage.length; row++) {
                for (int column = sideLength; column < newImage[0].length - sideLength; column++) {
                    newImage[row][column] = rotatedsquare[row][column - sideLength];
                }
            }
        } else {
            int sideLength = (originalImage.length - originalImage[0].length) / 2;
            for (int row = sideLength; row < newImage.length - sideLength; row++) {
                for (int column = 0; column < newImage[0].length; column++) {
                    newImage[row][column] = rotatedsquare[row - sideLength][column];
                }
            }
        }
        return newImage;
    }

    /*
     * Rotate the image right like above.
     */
    /**
     *
     * @param originalImage image to be rotated to the right 90 degrees.
     * @return rotated image.
     */
    public static int[][] rotateRight(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = FILL_VALUE;
            }
        }
        int[][] square = cropSquare(originalImage);
        int[][] rotatedsquare = rotateRightSquare(square);
        if (rotatedsquare.length == originalImage.length) {
            int sideLength = (originalImage[0].length - originalImage.length) / 2;
            for (int row = 0; row < newImage.length; row++) {
                for (int column = sideLength; column < newImage[0].length - sideLength; column++) {
                    newImage[row][column] = rotatedsquare[row][column - sideLength];
                }
            }
        } else {
            int sideLength = (originalImage.length - originalImage[0].length) / 2;
            for (int row = sideLength; row < newImage.length - sideLength; row++) {
                for (int column = 0; column < newImage[0].length; column++) {
                    newImage[row][column] = rotatedsquare[row - sideLength][column];
                }
            }
        }
        return newImage;
    }
    /**
     *
     * @param originalImage a square to be rotated right 90 degrees.
     * @return rotated square.
     */
    public static int[][] rotateRightSquare(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = originalImage[column][originalImage[0].length - row - 1];
            }
        }
        return newImage;
    }
    /**
     *
     * @param originalImage picture to be cropped into a square.
     * @return square.
     */
    public static int[][] cropSquare(final int[][] originalImage) {
        if (originalImage.length > originalImage[0].length) {
            int[][] square = new int[originalImage[0].length][originalImage[0].length];
            int sideLength = (originalImage.length - originalImage[0].length) / 2;
            for (int row = 0; row < originalImage[0].length; row++) {
                for (int column = 0; column < originalImage[0].length; column++) {
                    square[row][column] = originalImage[row + sideLength][column];
                }
            }
            return square;
        } else {
            int[][] square = new int[originalImage.length][originalImage.length];
            int sideLength = (originalImage[0].length - originalImage.length) / 2;
            for (int row = 0; row < originalImage.length; row++) {
                for (int column = 0; column < originalImage.length; column++) {
                    square[row][column] = originalImage[row][column + sideLength];
                }
            }
            return square;
        }
    }

    /*
     * Flip the image on the vertical axis across its center.
     */
    /**
     *
     * @param originalImage picture to be flipped on y axis.
     * @return flipped picture.
     */
    public static int[][] flipHorizontal(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = originalImage[originalImage.length - row - 1][column];
            }
        }
        return newImage;
    }

    /*
     * Flip the image on the horizontal axis across its center.
     */
    /**
     *
     * @param originalImage picture to be flipped on x axis.
     * @return flipped picture.
     */
    public static int[][] flipVertical(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = originalImage[row][originalImage[0].length - 1 - column];
            }
        }
        return newImage;
    }


    /**
     * Default amount to shift colors by. Not used by the testing suite, so feel free to change this
     * value.
     */
    public static final int DEFAULT_COLOR_SHIFT = 32;

    /**
     * Add red to the image.
     * <p>
     * This function <i>does not modify the original image</i>. It should also not generate any new
     * filled pixels.
     *
     * @param originalImage the image to add red to
     * @param amount the amount of red to add
     * @return the recolored image
     */
    public static int[][] moreRed(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, amount, RED_BYTE);
        return originalImage;
    }

    /*
     * Remove red from the image.
     */
    /**
     *
     * @param originalImage image to remove red from.
     * @param amount amount of red to remove.
     * @return recolored image.
     */
    public static int[][] lessRed(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, -amount, RED_BYTE);
        return originalImage;
    }

    /*
     * Add green to the image.
     */
    /**
    * @param originalImage the image to add green to
    * @param amount the amount of green to add
    * @return the recolored image
    */
    public static int[][] moreGreen(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, amount, GREEN_BYTE);
        return originalImage;
    }

    /*
     * Remove green from the image.
     */
    /**
     *
     * @param originalImage image to remove green from.
     * @param amount amount of green to remove.
     * @return recolored image.
     */
    public static int[][] lessGreen(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, -amount, GREEN_BYTE);
        return originalImage;
    }

    /*
     * Add blue to the image.
     */
    /**
     * @param originalImage the image to add blue to
     * @param amount the amount of blue to add
     * @return the recolored image
     */
    public static int[][] moreBlue(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, amount, BLUE_BYTE);
        return originalImage;
    }

    /*
     * Remove blue from the image.
     */
    /**
     *
     * @param originalImage image to remove green from.
     * @param amount amount of green to remove.
     * @return recolored image.
     */
    public static int[][] lessBlue(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, -amount, BLUE_BYTE);
        return originalImage;
    }

    /*
     * Increase the image alpha channel.
     */
    /**
     * @param originalImage the image to make more transparent
     * @param amount the amount of transparency to add
     * @return the recolored image
     */
    public static int[][] moreAlpha(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, amount, ALPHA_BYTE);
        return originalImage;
    }

    /*
     * Decrease the image alpha channel.
     */
    /**
     *
     * @param originalImage image to make less transparent.
     * @param amount amount of transparency to remove.
     * @return recolored image.
     */
    public static int[][] lessAlpha(final int[][] originalImage, final int amount) {
        colorShifter(originalImage, -amount, ALPHA_BYTE);
        return originalImage;
    }
    /**
     *
     * @param originalImage image to modify colors
     * @param amount amount to modify
     * @param shift color/alpha to modify
     * @return modified picture
     */
    public static int[][] colorShifter(final int[][] originalImage,
            final int amount, final int shift) {
        int[] colorPalette = new int[TOTAL_BYTES];
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = 0; column < originalImage[0].length; column++) {
                colorPalette[RED_BYTE] = (originalImage[row][column]) & MAX_COLOR;
                colorPalette[GREEN_BYTE] =
                        (originalImage[row][column] >> GREEN_CHANNEL) & MAX_COLOR;
                colorPalette[BLUE_BYTE] = (originalImage[row][column] >> BLUE_CHANNEL) & MAX_COLOR;
                colorPalette[ALPHA_BYTE] =
                        (originalImage[row][column] >> ALPHA_CHANNEL) & MAX_COLOR;
                colorPalette[shift] += amount;
                if (colorPalette[shift] > MAX_COLOR) {
                    colorPalette[shift] = MAX_COLOR;
                } else if (colorPalette[shift] < 0) {
                    colorPalette[shift] = 0;
                }
                int newcolor = ((colorPalette[ALPHA_BYTE] << ALPHA_CHANNEL)
                        | (colorPalette[BLUE_BYTE] << BLUE_CHANNEL)
                        | (colorPalette[GREEN_BYTE] << GREEN_CHANNEL)
                        | (colorPalette[RED_BYTE]));
                originalImage[row][column] = newcolor;
            }
        }
        return originalImage;
    }

    /**
     * The default resize factor. Not used by the testing suite, so feel free to change this value.
     */
    public static final int DEFAULT_RESIZE_AMOUNT = 2;

    /**
     * Shrink in the vertical axis around the image center.
     * <p>
     * An amount of 2 will result in an image that is half its original height. An amount of 3 will
     * result in an image that's a third of its original height. Any pixels shrunk in from off
     * screen should be filled with FILL_VALUE. This function <i>does not modify the original
     * image</i>.
     *
     * @param originalImage the image to shrink
     * @param amount the factor by which the image's height is reduced
     * @return the shrunken image
     */
    public static int[][] shrinkVertical(final int[][] originalImage, final int amount) {
        return null;
    }

    /*
     * Expand in the vertical axis around the image center.
     */
    /**
     *
     * @param originalImage original image.
     * @param amount amount to expand vertically.
     * @return expanded image.
     */
    public static int[][] expandVertical(final int[][] originalImage, final int amount) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length * amount];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = originalImage[row][column / amount];
            }
        }
        int[][] center = new int[originalImage.length][originalImage[0].length];
        int offset = (newImage[0].length * (amount - 1) / (amount * 2));
        for (int row = 0; row < center.length; row++) {
            for (int column = 0; column < center[0].length; column++) {
                center[row][column] = newImage[row][column + offset];
            }
        }
        return center;
    }

    /*
     * Shrink in the horizontal axis around the image center.
     */
    /**
    *
    * @param originalImage original image.
    * @param amount amount to shrink horizontally.
    * @return expanded image.
    */
    public static int[][] shrinkHorizontal(final int[][] originalImage, final int amount) {
        return null;
    }

    /*
     * Expand in the horizontal axis around the image center.
     */
    /**
    *
    * @param originalImage original image.
    * @param amount amount to expand horizontally.
    * @return expanded image.
    */
    public static int[][] expandHorizontal(final int[][] originalImage, final int amount) {
        int[][] newImage = new int[originalImage.length * amount][originalImage[0].length];
        for (int row = 0; row < newImage.length; row++) {
            for (int column = 0; column < newImage[0].length; column++) {
                newImage[row][column] = originalImage[row / amount][column];
            }
        }
        int[][] center = new int[originalImage.length][originalImage[0].length];
        int offset = (newImage.length * (amount - 1) / (amount * 2));
        for (int row = 0; row < center.length; row++) {
            for (int column = 0; column < center[0].length; column++) {
                center[row][column] = newImage[row + offset][column];
            }
        }
        return center;
    }

    /**
     * Remove a green screen mask from an image.
     * <p>
     * This function should remove primarily green pixels from an image and replace them with
     * transparent pixels (FILL_VALUE), allowing you to achieve a green screen effect. Obviously
     * this function will destroy pixels, but it <i>does not modify the original image</i>.
     * <p>
     * While this function is tested by the test suite, only extreme edge cases are used. Getting it
     * work work will with real green screen images is left as a challenge for you.
     *
     * @param originalImage the image to remove a green screen from
     * @return the image with the green screen removed
     */
    public static int[][] greenScreen(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = 0; column < originalImage[0].length; column++) {
                int red = (originalImage[row][column]) & MAX_COLOR;
                int green = (originalImage[row][column] >> GREEN_CHANNEL) & MAX_COLOR;
                int blue = (originalImage[row][column] >> BLUE_CHANNEL) & MAX_COLOR;
                if ((green == MAX_COLOR) && (red == 0) && (blue == 0)) {
                    newImage[row][column] = FILL_VALUE;
                } else {
                    newImage[row][column] = originalImage[row][column];
                }
            }
        }
        return newImage;
    }

    /**
     * A wild and mysterious image transform.
     * <p>
     * You are free to implement this in any way you want. It is not tested rigorously by the test
     * suite, but it should do something (change the original image) and <i>not modify the original
     * image</i>.
     * <p>
     * Call this function mystery. It should take only the original image as a single argument and
     * return a modified image.
     *
     * @param originalImage the image to perform a strange and interesting transform on
     * @return the image transformed in wooly and frightening ways
     */
    public static int[][] mystery(final int[][] originalImage) {
        int[][] newImage = new int[originalImage.length][originalImage[0].length];
        for (int row = 0; row < originalImage.length; row++) {
            for (int column = 0; column < originalImage[0].length; column++) {
                int red = (originalImage[row][column]) & MAX_COLOR;
                int green = (originalImage[row][column] >> GREEN_CHANNEL) & MAX_COLOR;
                int blue = (originalImage[row][column] >> BLUE_CHANNEL) & MAX_COLOR;
                int alpha = (originalImage[row][column] >> ALPHA_CHANNEL) & MAX_COLOR;
                red = MAX_COLOR - red;
                green = MAX_COLOR - green;
                blue = MAX_COLOR - blue;
                int newcolor = ((alpha << ALPHA_CHANNEL) | (blue << BLUE_CHANNEL)
                        | (green << GREEN_CHANNEL) | (red));
                newImage[row][column] = newcolor;
            }
        }
        return newImage;
    }
}
