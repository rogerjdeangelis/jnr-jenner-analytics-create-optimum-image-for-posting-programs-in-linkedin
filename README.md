# jnr-jenner-analytics-create-optimum-image-for-posting-programs-in-linkedin
Jenner Analytics create optimum image for posting programs in linkedin
    /*---
    c:/utl/jnr-jenner-analytics-create-optimum-image-for-posting-programs-in-linkedin.sas
    ---*/

    Jenner Analytics create optimum image for posting programs in linkedin

    Optimized image for LinkedIn
    https://tinyurl.com/2zs5ere9

    see
    https://tinyurl.com/yureskyn
    https://github.com/rogerjdeangelis/jnr-jenner-analytics-create-optimum-image-for-posting-programs-in-linkedin


    CONTENTS

      1  Save program code in d:/sas/spss.sas
      2  Python code to create optimum png for posting in linkedin
         Usage:
           text_to_linkedin_png(
              input_text_file=r"d:\sas\spss.sas",
              output_png=r"d:\png\linkedin.png",
              title="Jenner Analytics Open Source SPSS"
           );
      3  Output
           d:\png\linkedin.png
           see https://tinyurl.com/2zs5ere9
           https://github.com/rogerjdeangelis/jnr-jenner-analytics-create-optimum-image-for-posting-programs-in-linkedin/blob/main/linkedin.png


    /******************************************************************************************************************/
    /*  1  SAVE PROGRAM CIDE IN D:/SAS/SPSS.SAS                                                                       */
    /******************************************************************************************************************/

    /*--- SAVE THIS PROGRAM IN D:/SAS/SPSS.SAS ---*/

    %utlfkil(d:\sas\spss.sas);

    options syntaxcheck;
    data _null_;
      file "d:\sas\spss.sas";
      input;
      text = tranwrd(_infile_, '@@@@', ';;;;');
      put text;
    cards4;
    %jnr_spssBegin;
    cards4;
    GET FILE="d:/sav/have.sav".
    REGRESSION
    /VARIABLES=weight
      /DEPENDENT=age
      /METHOD=ENTER
      /SAVE PRED RESID.
    SAVE
    OUTFILE="d:\sav\want.sav".
    @@@@
    %jnr_spssEnd;
                   ANOVA (AGE)
    +----------+--------+--+-------+----+----+
    |          |  Sum of|df|   Mean|  F |Sig.|
    |          | Squares|df| Square|  F |Sig.|
    +----------+--------+--+-------+----+----+
    |Regression|     .74| 1|    .74|4.81|.116|
    |Residual  |     .46| 3|    .15|    |    |
    |Total     |    1.20| 4|       |    |    |
    +----------+--------+--+-------+----+----+
    ;;;;
    run;

    LOG:  10:24:14
    ==============

    NOTE: Copyright (c) 2026 Jenner Analytics Ltd., London, England.
    NOTE: Jenner v1.5.97 (build v1.5.97+921fdf5fb7.20261010T011618Z)
          Licensed to Roger DeAngelis, Serial 3BF7B3E6.
    NOTE: DATA _null_

    autexec started.

    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    NOTE: Library WORKX assigned path=d:\wpswrkx.
    NOTE: DATA workx.class

    NOTE: Processing inline DATALINES (19 lines)

    NOTE: Read 19 rows from DATALINES.
    NOTE: The data set WORKX.CLASS has 19 observations and 5 variables.
    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    NOTE: DATA _null_

    NOTE: DATA _null_ completed. Output written to FILE PRINT
    NOTE: Option SASAUTOS changed to c:/otojnr.
    NOTE: DATA _null_

    NOTE: Reading from fileref c:/jnr/runsas_selection.sas (c:/jnr/runsas_selection.sas)
        1 %utlfkil(d:\sas\spss.sas);
        2
        3 options syntaxcheck;
        4 data _null_;
        5   file "d:\sas\spss.sas";
        6   input;
        7   text = tranwrd(_infile_, '@@@@', ';;;;');
        8   put text;
        9 cards4;
       10 %jnr_spssBegin;
       11 cards4;
       12 GET FILE="d:/sav/have.sav".
       13 REGRESSION
       14 /VARIABLES=weight
       15   /DEPENDENT=age
       16   /METHOD=ENTER
       17   /SAVE PRED RESID.
       18 SAVE
       19 OUTFILE="d:\sav\want.sav".
       20 @@@@
       21 %jnr_spssEnd;
       22                ANOVA (AGE)
       23 +----------+--------+--+-------+----+----+
       24 |          |  Sum of|df|   Mean|  F |Sig.|
       25 |          | Squares|df| Square|  F |Sig.|
       26 +----------+--------+--+-------+----+----+
       27 |Regression|     .74| 1|    .74|4.81|.116|
       28 |Residual  |     .46| 3|    .15|    |    |
       29 |Total     |    1.20| 4|       |    |    |
       30 +----------+--------+--+-------+----+----+
       31 ;;;;
       32 run;

    NOTE: Read 32 rows from c:/jnr/runsas_selection.sas.
    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    NOTE: DATA _null_

    autoexec completed  10:24:14

    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    The file d:\sas\spss.sas does not exist
    NOTE: DATA _null_

    NOTE: Writing to fileref d:\sas\spss.sas (d:\sas\spss.sas)
    NOTE: Processing inline DATALINES (21 lines)

    NOTE: Read 21 rows from DATALINES.
    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds

    /******************************************************************************************************************/
    /*  2  PYTHON CODE TO CREATE OPTIMUM PNG FOR POSTING IN LINKEDIN                                                  */
    /******************************************************************************************************************/

    options set=PYTHONHOME "D:\py314";
    proc python;
    submit;
    from pathlib import Path
    from PIL import Image, ImageDraw, ImageFont

    WIDTH = 1080
    HEIGHT = 1350
    MARGIN = 80

    BG = (18, 18, 24)
    PANEL = (28, 30, 38)
    TEXT = (235, 235, 235)
    ACCENT = (90, 170, 255)


    def get_font(size):
        for name in [
            "consola.ttf",
            "C:/Windows/Fonts/consola.ttf",
            "arial.ttf",
            "C:/Windows/Fonts/arial.ttf",
        ]:
            try:
                return ImageFont.truetype(name, size)
            except OSError:
                pass
        return ImageFont.load_default()


    def text_to_linkedin_png(
        input_text_file,
        output_png,
        title="Text",
    ):
        text = Path(input_text_file).read_text(encoding="utf-8")

        # Remove indentation and blank-line clutter
        lines = [line.strip() for line in text.splitlines()]
        lines = [line for line in lines if line]

        img = Image.new("RGB", (WIDTH, HEIGHT), BG)
        draw = ImageDraw.Draw(img)

        title_font = get_font(48)
        text_font = get_font(32)
        footer_font = get_font(22)

        # Header
        draw.rectangle([(0, 0), (WIDTH, 130)], fill=PANEL)
        draw.text((MARGIN, 40), title, font=title_font, fill=(255, 255, 255))

        # Text panel
        top = 170
        bottom = HEIGHT - 100
        draw.rounded_rectangle(
            [(MARGIN, top), (WIDTH - MARGIN, bottom)],
            radius=24,
            fill=PANEL,
        )

        # Draw each stripped line
        x = MARGIN + 40
        y = top + 40

        for line in lines:
            draw.text((x, y), line, font=text_font, fill=TEXT)
            y += text_font.size + 14

        # Footer
        draw.text(
            (MARGIN, HEIGHT - 75),
            " ",
            font=footer_font,
            fill=(160, 160, 170),
        )

        # Left accent bar
        draw.rectangle([(0, 0), (12, HEIGHT)], fill=ACCENT)

        Path(output_png).parent.mkdir(parents=True, exist_ok=True)
        img.save(output_png, "PNG", optimize=True)

        print(f"Created: {output_png}")


    if __name__ == "__main__":
        text_to_linkedin_png(
            input_text_file=r"d:\sas\spss.sas",
            output_png=r"d:\png\linkedin.png",
            title="Jenner Analytics Open Source SPSS"
        );

    LIST: 10:37:09
    ==============

    Created: d:\png\linkedin.png

    LOG:  10:37:09
    ==============

    NOTE: Copyright (c) 2026 Jenner Analytics Ltd., London, England.
    NOTE: Jenner v1.5.97 (build v1.5.97+921fdf5fb7.20261010T011618Z)
          Licensed to Roger DeAngelis, Serial 3BF7B3E6.
    NOTE: DATA _null_

    autexec started.

    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    NOTE: Library WORKX assigned path=d:\wpswrkx.
    NOTE: DATA workx.class

    NOTE: Processing inline DATALINES (19 lines)

    NOTE: Read 19 rows from DATALINES.
    NOTE: The data set WORKX.CLASS has 19 observations and 5 variables.
    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    NOTE: DATA _null_

    LOG:  10:37:09
    NOTE: DATA _null_ completed. Output written to FILE PRINT
    NOTE: Option SASAUTOS changed to c:/otojnr.
    NOTE: DATA _null_

    NOTE: Reading from fileref c:/jnr/runsas_selection.sas (c:/jnr/runsas_selection.sas)
        1 options set=PYTHONHOME "D:\py314";
        2 proc python;
        3 submit;
        4 from pathlib import Path
        5 from PIL import Image, ImageDraw, ImageFont
        6
        7 WIDTH = 1080
        8 HEIGHT = 1350
        9 MARGIN = 80
       10
       11 BG = (18, 18, 24)
       12 PANEL = (28, 30, 38)
       13 TEXT = (235, 235, 235)
       14 ACCENT = (90, 170, 255)
       15
       16
       17 def get_font(size):
       18     for name in [
       19         "consola.ttf",
       20         "C:/Windows/Fonts/consola.ttf",
       21         "arial.ttf",
       22         "C:/Windows/Fonts/arial.ttf",
       23     ]:
       24         try:
       25             return ImageFont.truetype(name, size)
       26         except OSError:
       27             pass
       28     return ImageFont.load_default()
       29
       30
       31 def text_to_linkedin_png(
       32     input_text_file,
       33     output_png,
       34     title="Text",
       35 ):
       36     text = Path(input_text_file).read_text(encoding="utf-8")
       37
       38     # Remove indentation and blank-line clutter
       39     lines = [line.strip() for line in text.splitlines()]
       40     lines = [line for line in lines if line]
       41
       42     img = Image.new("RGB", (WIDTH, HEIGHT), BG)
       43     draw = ImageDraw.Draw(img)
       44
       45     title_font = get_font(48)
       46     text_font = get_font(32)
       47     footer_font = get_font(22)
       48
       49     # Header
       50     draw.rectangle([(0, 0), (WIDTH, 130)], fill=PANEL)
       51     draw.text((MARGIN, 40), title, font=title_font, fill=(255, 255, 255))
       52
       53     # Text panel
       54     top = 170
       55     bottom = HEIGHT - 100
       56     draw.rounded_rectangle(
       57         [(MARGIN, top), (WIDTH - MARGIN, bottom)],
       58         radius=24,
       59         fill=PANEL,
       60     )
       61
       62     # Draw each stripped line
       63     x = MARGIN + 40
       64     y = top + 40
       65
       66     for line in lines:
       67         draw.text((x, y), line, font=text_font, fill=TEXT)
       68         y += text_font.size + 14
       69
       70     # Footer
       71     draw.text(
       72         (MARGIN, HEIGHT - 75),
       73         " ",
       74         font=footer_font,
       75         fill=(160, 160, 170),
       76     )
       77
       78     # Left accent bar
       79     draw.rectangle([(0, 0), (12, HEIGHT)], fill=ACCENT)
       80
       81     Path(output_png).parent.mkdir(parents=True, exist_ok=True)
       82     img.save(output_png, "PNG", optimize=True)
       83
       84     print(f"Created: {output_png}")
       85
       86
       87 if __name__ == "__main__":
       88     text_to_linkedin_png(
       89         input_text_file=r"d:\sas\spss.sas",
       90         output_png=r"d:\png\linkedin.png",
       91         title="Jenner Analytics Open Source SPSS"
       92     );

    NOTE: Read 92 rows from c:/jnr/runsas_selection.sas.
    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.02 seconds
    NOTE: DATA _null_

    autoexec completed  10:37:09

    NOTE: DATA elapsed:
      wall  0.00 seconds
      cpu   0.00 seconds
    NOTE: Option SET changed to PYTHONHOME D:\py314.
    NOTE: PROC PYTHON step executing.
    NOTE: PROC PYTHON step completed.

    /******************************************************************************************************************/
    /*  3  OUTPUT                                                                                                     */
    /******************************************************************************************************************/

    https://tinyurl.com/2zs5ere9

    /*--- END ---*/
