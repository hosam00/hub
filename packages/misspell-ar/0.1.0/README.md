# Espanso Arabic Typos (misspell-ar)

An official [Espanso](https://espanso.org/) package designed to automatically fix common Arabic spelling and grammar mistakes on the fly, saving you time and ensuring professional text formatting.

Unlike standard spell-checkers that require you to click and correct, `misspell-ar` operates instantly in the background, auto-correcting your text the millisecond you press the spacebar.

## 🚀 Installation

Make sure you have Espanso installed on your system. Then, open your terminal and run the following command:

    espanso install misspell-ar
    espanso restart

## ✨ Features & Corrections

This dictionary targets frequent Arabic typing errors. It avoids the most dangerous context-dependent cases, but a small curated subset still relies on typical usage — when in doubt, review your text.

Currently, the package includes **4,950+ corrections** covering:

* **Taa Marbouta & Haa (التاء المربوطة والهاء):** Fixes common mix-ups (e.g., `ساعه` → `ساعة`, `لغه` → `لغة`, `الهضبه` → `الهضبة`).
* **Hamza on Alif (الهمزات):** Corrects missing or misplaced Hamzas on Alif (`أ`, `إ`, `آ`), including words with the definite article (e.g., `الاصغر` → `الأصغر`, `الامارات` → `الإمارات`, `انت` → `أنت`, `اخر` → `آخر`).
* **Tanween (التنوين):** Converts false Noun endings into proper Tanween (e.g., `شكرا` → `شكراً`, `دائما` → `دائماً`, `معا` → `معاً`).
* **Common Religious Phrases:** Ensures respectful and grammatically correct formatting of common phrases (e.g., `انشاء الله` → `إن شاء الله`, `اللهم صلي` → `اللهم صلِّ`, `الحمدلله` → `الحمد لله`).
* **ضاad / Zhaa (ض/ظ):** Corrects common mix-ups (e.g., `ضهر` → `ظهر`, `ضلم` → `ظلم`, `عضم` → `عظم`).
* **Alif Maqsura (الألف المقصورة):** Fixes `ى`/`ي` ending mistakes (e.g., `عيسي` → `عيسى`, `مصطفي` → `مصطفى`).
* **Other Common Typos:** Separates merged phrases, restores mid-word Hamzas, and more (e.g., `تسائل` → `تساؤل`, `هاذا` → `هذا`, `لاكن` → `لكن`).

### How it's built

Most corrections are **rule-generated** from a large frequency corpus of real Arabic text using conservative, meaning-preserving rules designed to avoid colliding with valid words:

- **Taa Marbouta → Haa:** only applied where (a) the noun stem is not itself a standalone word (reduces false hits like `فتحه` = "his opening" vs `فتحة` = "an opening") and (b) the corrected form is several times more frequent than the trigger in the corpus (drops rare junk like `مشابة`, keeping healthy pairs like `ساعة/ساعه`).
- **Hamza-drop with `ال`:** the definite article + hamza (`الأ`, `الإ`, `الآ`) → plain `الا` pairs are kept only when the hamza form clearly dominates in frequency, which excludes alif-wasl words (`استجابة`, `اعتراف`) where the bare form is the correct spelling.

The generator that produced this file lives in the source repository of this package (`scripts/gen.py`); this hub package ships only the generated dictionary. All matches use `word: true` where the trigger is a single word.

## 🛠️ Usage

There is no configuration required. Once installed and restarted, Espanso will quietly monitor your keystrokes. Just type normally in any application (browser, terminal, IDE, or chat app). If you type a known misspelling and press `Space` or `Enter`, it will instantly snap to the correct spelling.

## 🤝 Contributing

Arabic is a rich and complex language, and this dictionary is always growing! If you notice a common typo that is missing, contributions are highly encouraged.

To add a new word:
1. Fork the [Espanso Hub repository](https://github.com/espanso/hub).
2. Navigate to `packages/misspell-ar/`.
3. Open the `package.yml` file for the latest version.
4. Add your new match following this exact YAML format:
   ```yaml
     - trigger: "الكلمة_الخطأ"
       replace: "الكلمة_الصحيحة"
       word: true
   ```
5. Submit a Pull Request!

*Note: Please ensure new additions are unambiguous and do not accidentally overwrite valid words.*

## 📚 Attribution

The rule-generated portion is derived from the [FrequencyWords](https://github.com/hermitdave/FrequencyWords) Arabic corpus (content licensed under [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/)), which is itself derived from common open text sources (Wikipedia, OpenSubtitles, etc.).

## 👨‍💻 Author

Created and maintained by **Hossam Gamal** ([@hosam00](https://github.com/hosam00)).