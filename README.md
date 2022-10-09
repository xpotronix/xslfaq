# xslfaq
XSL, XSLT, FO FAQ from dpawson.co.uk

```xml
<xsl:stylesheet
  xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">

<xsl:output method="xml" indent="yes"/>

<xsl:template match="/">

  <xsl:for-each select="
    document('dp-f1.xml')/fa/a|
    document('dp-f2.xml')/fb/a[not(@name=document('dp-f1.xml')/fa/a/@name)]">
    
    <xsl:sort select="@name"/>
    
    <a name="{@name}">
      <xsl:value-of select="
        sum(document('dp-f1.xml')/fa/a[@name=current()/@name]|
        document('dp-f2.xml')/fb/a[@name=current()/@name])"/>
    </a>
   
  </xsl:for-each>

</xsl:template>

</xsl:stylesheet>
```


