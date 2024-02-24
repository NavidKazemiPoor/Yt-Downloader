from pytube import YouTube
# select specific resolution and format
def select_video(url):
    yt = YouTube(url)
    streams = yt.streams.filter(progressive=True)
    for i in streams:
        print(f"itag:{i.itag} - Resolution: {i.resolution} - type: {i.mime_type}")
    selected_itag = int(input("Enter itag:\t"))
    for stream in streams:
       if selected_itag == stream.itag:            
            break
    print("--- Summery ---")
    print(f"\n DO YOU WANT TO DOWNLOAD THIS?\n")
    print(f"- title: \"{yt.title}\"")
    print(f"- length: {yt.length/60:.2f}min")
    print(f"- format: {stream.mime_type}")
    print(f"- Resolution: {stream.resolution}")
    print(f"- views: {yt.views}")
    selected = input("\ninput \"Y/N\"\t")
    if selected.lower() == 'y':
        download_video(yt,stream)
        return
    main()
#downloading yt video
def download_video(yt,stream):
    yt.register_on_progress_callback(download_progress)
    yt.register_on_complete_callback(download_complete)
    print('Downloading Started... wait until end')
    stream.download()
#download percentage
def download_progress(stream,chunk,bytes_remain):
        total_size =stream.filesize
        bytes_downloaded = total_size -bytes_remain
        percentage_of_completion = bytes_downloaded / total_size * 100
        print(f"{percentage_of_completion:.2f}%")
# if download complete
def download_complete(stream,file_handle):
    print("\nDownloaded.\n")
    main()
    
def main():
    print("--- Welcome To Yt Downloader --- ")
    url = input("Enter Video URL:\t")
    select_video(url)
    
if __name__ == '__main__':
    main()
