# P6 형식의 PPM 파일을 P3 형식으로 바꾸는 간단한 코드

def create_p3_file(p3_file, width, height, maxval):
    """
    P3 형식의 빈 파일을 생성하는 함수
    """
    with open(p3_file, 'w') as out:
        out.write("P3\n")
        out.write(f"{width} {height}\n")
        out.write(f"{maxval}\n")


def convert_p6_to_p3(p6_file, p3_file):
    with open(p6_file, 'rb') as f:  # 바이너리 읽기
        lines = []

        # 헤더 읽기 (매직 넘버, 주석, 너비/높이, max값)
        while len(lines) < 3:
            line = f.readline()
            if not line.startswith(b'#'):  # 주석(#)은 건너뜀
                lines.append(line.strip())

        width, height = map(int, lines[1].split())
        maxval = int(lines[2])

        # P3 파일이 없으면 생성
        create_p3_file(p3_file, width, height, maxval)

        # 픽셀 데이터 읽기 (RGB 각각 1바이트)
        pixel_data = f.read()

    # P3 파일에 픽셀 데이터 추가
    with open(p3_file, 'a') as out:
        for i in range(0, len(pixel_data), 3):
            r = pixel_data[i]
            g = pixel_data[i + 1]
            b = pixel_data[i + 2]
            out.write(f"{r} {g} {b}\n")


# 실행 부분
if __name__ == "__main__":
    # P6 파일 경로와 P3 파일 경로를 지정
    p6_file = "/home/data/colorP6File.ppm"
    p3_file = "/home/s32201238/Git_0507/colorP3File.ppm"  # 수정된 경로

    convert_p6_to_p3(p6_file, p3_file)
