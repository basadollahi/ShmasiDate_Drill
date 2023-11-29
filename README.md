قبل از هر چیز باید بگم این کد در apache-drill-1.21.1 تست شده


1-اول در CMD دستورات زیر را اجرا می کنیم

mkdir "%userprofile%\drill"

mkdir "%userprofile%\drill\udf"

mkdir "%userprofile%\drill\udf\registry"

mkdir "%userprofile%\drill\udf\tmp"

mkdir "%userprofile%\drill\udf\staging"

takeown /R /F "%userprofile%\drill"

2-jar های زیر را در مسیر "%userprofile%\drill\udf\staging" کپی می کنید

drill-simple-mask-1.3.jar

drill-simple-mask-1.3-sources.jar

3-jar های زیر را در مسیر "apache-drill-1.21.1\jars\3rdparty%\drill\udf\staging" کپی می کنید

Shamsidate.jar


4- وارد apache-drill-1 می شوید و دستور زیر را اجرا می کنید

CREATE FUNCTION USING JAR 'drill-simple-mask-1.3.jar';

5-سپس یکبار برنامه را باز و بسته کرده



6-وارد apache-drill-1 می شوید و دستور زیر را اجرا می کنید

select
    TO_CHAR(3125365, '#,###.###') as Price,
    m2s(cast (hire_date as date)) as miladi2Shamsi,
    m2sf(cast (hire_date as date),'l m F  Y' ) as dd
FROM cp.`employee.json` aa
where cast (hire_date as date) between
    s2m('1374/09/10') and s2m('1375/09/10') ;
