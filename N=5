
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import mne
from mne.preprocessing.nirs import (
    optical_density,
    beer_lambert_law,
    temporal_derivative_distribution_repair
)
import matplotlib as mpl
import matplotlib.colors as mcolors
from mne.preprocessing.nirs import scalp_coupling_index
import re
from collections import Counter

# raw = mne.io.read_raw_snirf("C:\\Users\\USER\\Desktop\\test data\\250903_1627_sminji_test_NS_Unknown.snirf")

# 여러 SNIRF 파일 경로
file_list = [
    r"C:\\Users\\USER\\Desktop\\test data\\250921_1700_20250921_NS_SoohyunChoi.snirf",
    r"C:\\Users\\USER\\Desktop\\test data\\250921_1611_20250921_NS_HobinHwang.snirf",
    r"C:\\Users\\USER\\Desktop\\test data\\250921_1553_20250921_NS_JunyongJang.snirf",
    r"C:\\Users\\USER\\Desktop\\test data\\250921_1533_20250921_NS_YoungseokChoi.snirf",
    r"C:\\Users\\USER\\Desktop\\test data\\250921_1513_20250921_NS_JihoHa2.snirf",
]

# raw 객체를 dict로 저장 (파일명 기준)
raws = {}
names=["CSH", "HHB", "JJY", "CYS", "HJH"]
for i,f in enumerate(file_list):
    # name = f.split("\\")[-1]  # 파일명만 추출
    raws[names[i]] = mne.io.read_raw_snirf(f, preload=True)

# 확인
for name, raw in raws.items():
    print(name, raw)

