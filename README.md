# utl_collapsing_column_and_rows_while_filling_in_missing_values
Collapsing columns and rows while filling in missing values. Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Collapsing columns and rows while filling in missing values

    Same result in WPS and SAS

    Nice example

    github
    https://tinyurl.com/y9d4q2b2
    https://github.com/rogerjdeangelis/utl_collapsing_column_and_rows_while_filling_in_missing_values

    Reeza profile
    https://communities.sas.com/t5/user/viewprofilepage/user-id/13879

    see
    https://tinyurl.com/yatlah2a
    https://communities.sas.com/t5/SAS-Visual-Analytics/Need-help-with-copying-data-into-missing-fields-using-SAS-VA-7-3/m-p/463033


    INPUT
    =====

    WORK.HAVE total obs=6

       RECORD    NAME      ACTIVITY    YEAR    MONTH

         1       snoopy      123
         1                             2018     JAN
         2       bob         456
         2                             2018     FEB
         3       raul        123
         3                             2018     MAR

    EXAMPLE OUTPUT

      RECORD    NAME      ACTIVITY    YEAR    MONTH

        1       snoopy      123       2018     JAN
        2       bob         456       2018     FEB
        3       raul        123       2018     MAR



    PROCESS
    =======

    data want;
    update have(obs=0)  have;
    by record;
    run;


    OUTPUT
    ======

    WORK.WANT total obs=3

       RECORD    NAME      ACTIVITY    YEAR    MONTH

         1       snoopy      123       2018     JAN
         2       bob         456       2018     FEB
         3       raul        123       2018     MAR

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

    data have;
    input  (Record Name Activity Year Month) ($);
    cards4;
    1 snoopy 123 . .
    1 . . 2018 JAN
    2 bob 456 . .
    2 . . 2018 FEB
    3 raul 123 . .
    3 . . 2018 MAR
    ;;;;
    run;quit;

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    data want;
    update have(obs=0)  have;
    by record;
    run;

    %utl_submit_wps64('
    libname wrk sas7bdat "%sysfunc(pathname(work))";
    data want;
    update wrk.have(obs=0)  wrk.have;
    by record;
    run;quit;
    proc print;
    run;quit;
    ');
