# きららファンタジア字幕置換ツール

# Kirara Fantasia Auto Subtitle Patcher

## What is it?

This is a toolset for replacing the original Japanese text of Kirara Fantasia's story video into other languages.  
きららファンタジアの字幕を抽出し、文字部分を差し替えるツールである。  
Sample ouput:(generated by ver2.0)  
効果例：

-   English Subtitled:
    [![IMAGE ALT TEXT](http://img.youtube.com/vi/Z8BytfESak0/0.jpg)](https://www.youtube.com/embed/Z8BytfESak0 "CameraMaster")
-   Korean Subtitled:
    [![IMAGE ALT TEXT](http://img.youtube.com/vi/_6IlXAgpsEs/0.jpg)](https://www.youtube.com/embed/_6IlXAgpsEs "CameraMaster")

## Download

-   [for Windows](https://drive.google.com/open?id=1l-ITHCYr_9z4bCnXOJFNTCCkmTM-Sng6)

## Tutorial

[日本語版はここ](https://github.com/kirafanautodec/Kirafan_AutoSub/blob/master/README_JP.md)  
[中文说明看此处](https://github.com/kirafanautodec/Kirafan_AutoSub/blob/master/README_CN.md)

### Installiton

-   If you are using windows, download the pre-built binaries.
-   If you are using Linux or MacOS, clone this repository to a clean directory.  
    And install the dependences below:  
     - python (version 3) - python libraries - pillow - numpy - opencv-python - ffmpeg

### Usage

1. Record  
   Record a Kirara Fantasia story video, and copy it to an empty folder of your PC. - The folder name and video names **must not** include any **non-ansi** characters. - It is recommend to record by iOS built-in recording function. - You should turn on audio and check if audio is recorded. - When recording, make sure to include the first **transition** from 図書館 to Story, since transition will be an important sign for detecting start and end of each section. - Click **Auto Button** after the first sentence of section are shown fully. - You can record all videos of one chapter continually, since this tool will crop them automatically, but we recommend to record 5 ~ 10 videos at one time.
1. Crop  
   Drag the record video into Kirafan_AutoSub.exe, and select 1 (Crop). - on Linux, run `python AutoSub.py <video_file>` instead. - This procedure will detect transition between sections and automatically seperate them. - It will create a folder named `<video_file>_seq_video`, and the seperated sections are named `0001.mp4`, `0002.mp4` and so on. - In case you recorded 1~5.mp4 and 6~10.mp4, run for them respectively, and rename the videofile manually in `6~10.mp4_seq_video` to `0006.mp4`, `0007.mp4` and so on. After that copy those files into the same folder for consequence procedure.
1. Analysis and Label  
   Drag the **folder** containing `0001.mp4` ... into `Kirafan_AutoSub.exe`, and select 2 (Analysis). - on Linux, run `python AutoSub.py <folder>` instead. - The program will ask your targer language, input one from `en`, `jp`, `cn`, `ko`. - This procedure will analysis and label texts in videos, and generate a `krfss` file and a image folder for each video in `autosub` folder.
1. Translate  
   Edit those `krfss` files by **Krfss_Editor** - Refer the tutorial of [Krfss_Editor](https://github.com/kirafanautodec/Krfss_Editor).
1. Patch  
   Drag the **folder** containing `0001.mp4` ... into `Kirafan_AutoSub.exe`, and select 3 (Patch). - This procedure will apply the subtile file `krfss` and automatically patch them into videos. - It will generate files like `0001.mp4.autosubed.mp4`. - Besides, it will generate a `videolist.txt` file for video concatenating.
1. Concatenate(Optional)
    - Edit `videolist.txt` to add or remove some files to concat.
    ```
    file '0001.mp4.autosubed.mp4'
    file '0002.mp4.autosubed.mp4'
    ......
    ```
    - If you want to insert Openning/Ending, you must convert them before you copy them and add to `videolist.txt`
        - To convert a video, drag it into `Kirafan_AutoSub.exe` and select 5 (Convert).
        - The video after convertion is named `<video_name>.cvt.mp4`.
        - In case you have to adjust aspect ratio or audio gain manually, refer to ffmpeg toturial.
    - Drag the **folder** containing `0001.mp4` ... into `Kirafan_AutoSub.exe`, and select 4 (Concat).
    - The `output.mp4` is the final video.
