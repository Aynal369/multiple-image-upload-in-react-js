# multiple-image-upload-in-react-js
  1. Add two useState. 1st (empty string) and 2nd [empty array]
  2. In input fields set onChange funtion
  3. Under onChange funtion add this code
  ### For Cloudinary
  ```
  const imgFiles = e.target.files;
    let imgArr = [];
    for (let i = 0; i < imgFiles.length; i++) {
      let imageData = new FormData();
      imageData.append("file", imgFiles[i]);
      imageData.append("upload_preset", "your upload preset here");
      imageData.append("cloud_name", "your cloud name here");
      axios
        .post(
          "https://api.cloudinary.com/v1_1/aynal369/image/upload",
          imageData
        )
        .then((res) => {
          1st(res.data.url);  // set1st
          imgArr.push(res.data.url);
          2nd(imgArr); // set2nd
        })
        .catch((err) => {
          console.log(err);
        });
    }
  ```
  ### For Imgbb
  ```
   const imgFiles = e.target.files;
    let imgArr = [];
    for (let i = 0; i < imgFiles.length; i++) {
      let imageData = new FormData();
      imageData.set("key", "your imgbb key here");
      imageData.append("image", imgFiles[i]);
      axios
        .post("https://api.imgbb.com/1/upload", imageData)
        .then((res) => {
          1st(res.data.data.display_url); // set1st
          imgArr.push(res.data.data.display_url);
          2nd(imgArr); // set2nd
        })
        .catch((err) => {
          console.log(err);
        });
    }
  ```
  4. Now your handleSubmit function share 1st and 2nd useState.
  
  
  ** I am not a huge expert. Please let me know if there is any mistake in the code **
