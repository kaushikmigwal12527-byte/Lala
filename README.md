from moviepy.editor import AudioFileClip, ImageClip, concatenate_videoclips

def create_music_video(audio_path, image_paths, output_path, image_duration=5):
    # Load the audio clip
    audio_clip = AudioFileClip(audio_path)
    
    # Create video clips from images
    image_clips = []
    for img_path in image_paths:
        img_clip = ImageClip(img_path).set_duration(image_duration)
        image_clips.append(img_clip)
    
    # Concatenate image clips
    video_clip = concatenate_videoclips(image_clips, method="compose")
    
    # Set the audio to the video clip and set duration to audio length
    video_clip = video_clip.set_audio(audio_clip).set_duration(audio_clip.duration)
    
    # Write the result to a file
    video_clip.write_videofile(output_path, fps=24)

if __name__ == "__main__":
    # Replace with your audio and images
    audio_file = "song.mp3"
    images = ["image1.jpg", "image2.jpg", "image3.jpg"]  # Replace with your image files
    
    output_file = "music_video.mp4"
    
    create_music_video(audio_file, images, output_file)
    
