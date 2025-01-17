# BDF Parser

[![MIT License](https://img.shields.io/github/license/tomchen/bdfparser)](https://github.com/tomchen/bdfparser/blob/master/LICENSE "MIT License")

BDF (Glyph Bitmap Distribution Format) Bitmap Font File Parser (Python).

## Usage

```python
BdfParserObject = BdfParser(<FONT_FILE_PATH>)
BdfParserObject.{getCharBmpByUnicode|getCharHexByUnicode|getCharHexByUnicode|getGlyphInfo}(<UNICODE_DECIMAL>)
```

## Example

(see also [example.py](https://github.com/tomchen/bdfparser/blob/master/example.py))

Import library and instantiation:

```python
import bdfparser as bp
bpo = bp.BdfParser('example_fonts/bdf/SimSun-14.bdf')
```

Get binary representation string of bitmap of the character "的":

```python
bpo.getCharBmpByUnicode(30340)
```

Get hex representation string of bitmap of the character "的":

```python
bpo.getCharHexByUnicode(30340)
```

Get hex representation string in bytes of bitmap of the character "的":

```python
bpo.getCharHexByUnicode(30340).hex()
```

Get glyph information:

```python
bpo.getGlyphInfo(30340)
```

The above script returns:

```python
{'dwx0': 14, 'bbW': 12, 'bbH': 14, 'bbXOff': 1, 'bbYOff': -2, 'bitmap': '2100\n2100\n41F0\nFA10\n8C10\n8810\n8910\nF890\n8890\n8810\n8810\n8810\nF810\n8860', 'outputW': 14, 'outputH': 15, 'shadowedOutputW': 15, 'shadowedOutputH': 16, 'glowedOutputW': 16, 'glowedOutputH': 17}
```

Get binary representation of bitmap of the character "￣"

```python
bpo.getCharBmpByUnicode(65507)
```

Get binary representation of bitmap of the character "©" -- "©" does not exist in some font, and does not exist in GBK, therefore it throws an error:

```python
bpo.getCharBmpByUnicode(169)
```

Get the declared font name:

```python
bpo.getFontName()
```

## Other tools
* [Example .bdf fonts](https://github.com/tomchen/bdfparser/tree/master/example_fonts/bdf):
  * GNU Unifont ([Wikipedia article](https://en.wikipedia.org/wiki/GNU_Unifont); [Homepage](https://unifoundry.com/unifont/index.html)): Unicode font (intended to support "all" common languages)
  * M+ FONTS ([Wikipedia article](https://en.wikipedia.org/wiki/M%2B_FONTS); [Homepage](https://mplus-fonts.osdn.jp/about-en.html)): Japanese font
  * HanWangYanKai 王漢宗自由字型顏體 ([Chinese Wikipedia article](https://zh.wikipedia.org/wiki/%E7%8E%8B%E6%BC%A2%E5%AE%97%E8%87%AA%E7%94%B1%E5%AD%97%E5%9E%8B); [download .ttf](https://github.com/hepochen/fonts/raw/master/gpl-cjk-fonts/wang/wt064.ttf)): Traditional Chinese font
  * See also some typical but non-free, fair-used Chinese fonts in [another repo](https://github.com/might-and-magic/fnt-generator#other-tools)
* [otf2bdf](https://github.com/tomchen/bdfparser/tree/master/tools/otf2bdf): OpenType to BDF Converter. Just an archive. Not written by me.

## Projects that use this library

[FNT Generator](https://github.com/might-and-magic/fnt-generator): Might and Magic 6 7 8 and Heroes 3 font File Generator in Python. Another project of mine

## License

* Python code is written by me (Tom CHEN) and is released under the MIT License.
* [otf2bdf](https://github.com/tomchen/bdfparser/tree/master/tools/otf2bdf): see its page.
* Example .bdf fonts:
  * GNU Unifont: [GNU General Public License v2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html), by Roman Czyborra, Paul Hardy, part of the GNU Project
  * M+ FONTS: [a free license](https://mplus-fonts.osdn.jp/about-en.html#license), designed by Coji Morishita
  * HanWangYanKai 王漢宗自由字型顏體: [GNU General Public License v2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html), by 王漢宗
  * Other fonts are proprietary, and are used non-commercially and fairly