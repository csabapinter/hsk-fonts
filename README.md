# HSK Font Subsets

## Summary

Lightweight subets of four font families that keep only the HSK 1-9 characters and some of their related components. List of codepoints can be found in `component-codepoints.txt`. 
All four subsets cover all words in HSK 1-9 requirements, but only BabelStone Han covers their subcomponents as well.

## Coverage

Coverage counts reference `component-codepoints.txt` (3,484 codepoints).

- BabelStone Han subset: 3,484 covered / 0 missing.
- Source Han Serif subset: 3,388 covered / 96 missing (gaps start around U+2000E in CJK Extension B).
- Long Cang subset: 3,168 covered / 316 missing (first gaps U+2E80–U+2EBC).
- ZCOOL XiaoWei subset: 3,168 covered / 316 missing (same missing set as Long Cang).
- ZCOOL KuaiLe subset: 3,168 covered / 316 missing (gaps begin at U+2E80 in the CJK Radicals Supplement range)
- ZCOOL QingKe HuangYou subset: 3,174 covered / 310 missing (gaps begin at U+2E80 in the CJK Radicals Supplement range)


## Reproducing the BabelStone Han Subset

Dependencies: Python 3 with FontTools (which provides `pyftsubset`) and Brotli for WOFF2 output, install via `python3 -m pip install --upgrade fonttools brotli`.
Download BabelStoneHan.ttf from: https://www.babelstone.co.uk/Fonts/Han.html 

Generate subset:

```
python3 -m fontTools.subset fonts/babelstone_han/BabelStoneHan.ttf \
  --output-file=fonts/babelstone_han/BabelStoneHan-subset.woff2 \
  --flavor=woff2 \
  --unicodes-file=component-codepoints.txt \
  --layout-features='*'
```

## Licensing

- `long_cang/LongCang-Regular-subset.woff2`: subset of Long Cang (Hanyi). Licensed under SIL Open Font License 1.1 (`long_cang/OFL.txt`). The “Long Cang” name is reserved, so this build keeps the `-subset` suffix to comply with the OFL rename requirement.
- `source_han_serif/SourceHanSerif-subset.woff2`: subset of Source Han Serif SC ExtraLight (Adobe/Google). Licensed under SIL OFL 1.1 (`source_han_serif/LICENSE.txt`).
- `zcool_xiaowei/ZCOOLXiaoWei-Regular-subset.woff2`: subset of ZCOOL XiaoWei. Licensed under SIL OFL 1.1 (`zcool_xiaowei/OFL.txt`).
- `zcool_kuaile/ZCOOLKuaiLe-Regular-subset.woff2`: subset of ZCOOL KuaiLe. Licensed under SIL OFL 1.1 (`zcool_kuaile/OFL.txt`).
- `zcool_qingke_huangyou/ZCOOLQingKeHuangYou-Regular-subset.woff2`: subset of ZCOOL QingKe HuangYou. Licensed under SIL OFL 1.1 (`zcool_qingke_huangyou/OFL.txt`).
- `babelstone_han/BabelStoneHan-subset.woff2`: subset of BabelStone Han (© Arphic Technology Co., Ltd. and Andrew West). Licensed under the Arphic Public License 1.0 (`babelstone_han/APL.txt`).
- All subsets involve only glyph removal plus WOFF2 conversion based on `component-codepoints.txt`; no outlines were modified. When redistributing, include the relevant license file(s) alongside the fonts.
