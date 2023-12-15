Part 1
**getDownloadUrl() function is deprecated**
**Complete the video first, then replace the ref.putfile(imgUri) block of code with this**
ref.putFile(imgUri).addOnSuccessListener(new OnSuccessListener<UploadTask.TaskSnapshot>() {
    @Override
    public void onSuccess(UploadTask.TaskSnapshot taskSnapshot) {
        dialog.dismiss();
        Toast.makeText(getApplicationContext(), "Image uploaded", Toast.LENGTH_SHORT).show();
        //Get the download URL
        ref.getDownloadUrl().addOnSuccessListener(new OnSuccessListener<Uri>() {
            @Override
            public void onSuccess(Uri downloadUrl) {
                // Use the download URL to create an ImageUpload object
                ImageUpload imageUpload = new ImageUpload(txtImageName.getText().toString(), downloadUrl.toString());
                // Push the data to the database
                String uploadId = mDatabaseRef.push().getKey();
                mDatabaseRef.child(uploadId).setValue(imageUpload);
            }
        });
    }
})


Part 2
List of some things to do thats not included in video. This list may not be complete.
1. Add firebase authentication API
2. Add firebase storage API
3. include bumptech in build.gradle.kts(:app) in dependencies block. Need to paste: implementation("com.github.bumptech.glide:glide:4.16.0")
**WATCH THE VIDEO until the point where you have to use tvImageName for the first time in ImageListAdapter.java**
4. In ImageListAdapter.java, need to import tvImageName by copy/paste import static com.example.(your project name).tvImageName;
