import yt_dlp
import os

# Ensure the "Audio" folder exists
audio_path = r'C:'      #Enter manually the folder's path to save the audio file
os.makedirs(audio_path, exist_ok=True)

def get_download_type():
    print("\nChoose what you want to download:")
    print("1.  Video")
    print("2.  Audio (High Quality)")
    
    choice = input("Enter your choice (1-2): ")
    return choice

def get_video_quality():
    print("\nChoose video quality:")
    print("1. 360p")
    print("2. 480p")
    print("3. 720p (HD)")
    print("4. 1080p (Full HD)")
    
    choice = input("Enter your choice (1-4): ")

    quality_map = {
        "1": "bestvideo[height<=360]+bestaudio/best[height<=360]",
        "2": "bestvideo[height<=480]+bestaudio/best[height<=480]",
        "3": "bestvideo[height<=720]+bestaudio/best[height<=720]",
        "4": "bestvideo[height<=1080]+bestaudio/best[height<=1080]"
    }

    return quality_map.get(choice, "bestvideo[height<=720]+bestaudio/best[height<=720]")  # Default 720p

def download_video(url, quality):
    ydl_opts = {
        'format': quality,
        'merge_output_format': 'mp4',
        'outtmpl': r'C:\Users\souvi\Downloads\%(title)s.%(ext)s'
    }

    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download([url])

def download_audio(url):
    ydl_opts = {
        'format': 'bestaudio/best',  # Best quality audio
        'outtmpl': rf'C:\Users\souvi\Downloads\Audio\%(title)s.%(ext)s',
        'postprocessors': [{
            'key': 'FFmpegExtractAudio',
            'preferredcodec': 'mp3',  # You can change this to 'm4a' or 'wav'
            'preferredquality': '320'  # High-quality audio (320kbps)
        }]
    }

    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        ydl.download([url])

if __name__ == "__main__":
    video_url = input("Enter YouTube video URL: ")
    choice = get_download_type()

    if choice == "1":
        quality = get_video_quality()
        download_video(video_url, quality)
        print("\n Video Download Complete! Saved in Downloads folder.")
    elif choice == "2":
        download_audio(video_url)
        print("\n Audio Download Complete! Saved in 'Downloads/Audio' folder.")
    else:
        print("\n Invalid choice! Please enter 1 or 2.")
