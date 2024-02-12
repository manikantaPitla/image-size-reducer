# Image Size Reducer

A utility to reduce the quality of images

## Installation

You can install the package via npm or yarn:

```bash
npm install image-size-reducer
```

or

```bash
yarn add image-size-reducer
```

## Usage

```js
import reduceQuality from "image-size-reducer";

// Example usage
const handleFileChange = async (event) => {
  const file = event.target.files[0];
  try {
    const { imageFile, data } = await reduceQuality(file);

    //imageFile (imageFile after reduction)

    //data (data of image size before and after reduction )
    // {
    //   actualSize: "14.67 MB";
    //   reducedSize: "1.44 MB";
    // }

    // Do something with the reduced imageFile and data
  } catch (error) {
    console.error("Error:", error);
  }
};

return <input type="file" accept="image/*" onChange={handleFileChange} />;
```

The reduceQuality function takes a File object as input and returns a Promise that resolves to a reduced-quality image File. By default, it reduces the quality to 0.2, but if the width of the image is less than 300 pixels, it increases the quality to 0.8 to preserve more details.

You can also specify the quality parameter explicitly:

```js
const { imageFile, data } = await reduceQuality(file, 0.5);
```

The data object contains information about the actual size of the original file and the reduced size after compression.

## License

This project is licensed under the ISC License - see the LICENSE file for details.
