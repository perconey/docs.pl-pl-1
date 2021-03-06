---
title: "LINQ do XML-Przegląd klasy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f22f1b7e4f94acda3a9279baf92fbce0840e55ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ do XML-Przegląd klasy (Visual Basic)
Ten temat zawiera listę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klas w <xref:System.Xml.Linq> przestrzeni nazw oraz krótki opis każdego z nich.  
  
## <a name="linq-to-xml-classes"></a>LINQ do XML klas  
  
### <a name="xattribute-class"></a>Klasa XAttribute  
 <xref:System.Xml.Linq.XAttribute>reprezentuje atrybut XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [XAttribute klasy Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>Klasa XCData  
 <xref:System.Xml.Linq.XCData>reprezentuje węzeł tekstowy CDATA.  
  
### <a name="xcomment-class"></a>Klasa XComment  
 <xref:System.Xml.Linq.XComment>reprezentuje komentarz XML.  
  
### <a name="xcontainer-class"></a>Klasa XContainer  
 <xref:System.Xml.Linq.XContainer>jest to abstrakcyjna klasa podstawowa dla wszystkich węzłów, które mogą mieć węzłów podrzędnych. Następujące klasy pochodzi od <xref:System.Xml.Linq.XContainer> klasy:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>Klasa XDeclaration  
 <xref:System.Xml.Linq.XDeclaration>reprezentuje deklaracji XML. Deklaracja XML służy do deklarowania wersji XML i kodowania dokumentu. Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny. Jeśli dokument jest autonomicznym, nie ma żadnych deklaracji znaczników zewnętrznych, w zewnętrznej definicji DTD lub w jednostce parametru zewnętrzne odwołanie z podzestawu wewnętrznego.  
  
### <a name="xdocument-class"></a>Klasy XDocument  
 <xref:System.Xml.Linq.XDocument>reprezentuje dokumentu XML. Aby uzyskać szczegółowe informacje i przykłady, zobacz [klasy XDocument — Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>Klasa XDocumentType  
 <xref:System.Xml.Linq.XDocumentType>reprezentuje dokumentu typu Definition (definicja DTD dokumentu XML).  
  
### <a name="xelement-class"></a>Klasy XElement — klasa  
 <xref:System.Xml.Linq.XElement>reprezentuje XML element. Aby uzyskać szczegółowe informacje i przykłady, zobacz [klasy XElement klasy Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>Klasa XName  
 <xref:System.Xml.Linq.XName>reprezentuje nazwy elementów (<xref:System.Xml.Linq.XElement>) i atrybuty (<xref:System.Xml.Linq.XAttribute>). Aby uzyskać szczegółowe informacje i przykłady, zobacz [klasy XDocument — Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Umożliwia nazw XML równie proste, jak to możliwe. Ze względu na złożoność nazwy XML są często uważane zaawansowane tematu w kodzie XML. Można przypuszczać, że ta złożoności pochodzi nie z przestrzeni nazw, deweloperom używany regularnie programowania, ale z prefiksy przestrzeni nazw. Prefiksy Namespace może być przydatna, aby zmniejszyć naciśnięcia klawiszy wymagane podczas wprowadzania danych XML lub aby ułatwić XML. Jednak prefiksy są często tylko skrót przy użyciu pełnego przestrzeni nazw XML i nie są wymagane w większości przypadków. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]upraszcza nazw XML, rozwiązując wszystkie prefiksy do ich odpowiednich przestrzeni nazw XML. Prefiksy są dostępne, jeśli są wymagane przez <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metody.  
  
 Jest to możliwe, jeśli to konieczne, aby formant prefiksy przestrzeni nazw. W niektórych sytuacjach podczas pracy z innymi systemami XML, takiego jak XSLT lub XAML, należy kontrolować prefiksy przestrzeni nazw. Na przykład jeśli wyrażenie XPath, która korzysta z prefiksy przestrzeni nazw i jest osadzony w arkusz stylów XSLT, należy się upewnić, że dokument XML jest serializowany z prefiksy przestrzeni nazw, które pasują do wyrażenia XPath.  
  
### <a name="xnamespace-class"></a>Klasa XNamespace  
 <xref:System.Xml.Linq.XNamespace>reprezentuje obszar nazw dla <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>. Przestrzenie nazw są składnika <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>Klasa XNode  
 <xref:System.Xml.Linq.XNode>jest klasą abstrakcyjną, reprezentujący węzły drzewa XML. Następujące klasy pochodzi od <xref:System.Xml.Linq.XNode> klasy:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>Klasa XNodeDocumentOrderComparer  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>zapewnia funkcje do porównania węzły ich kolejności dokumentu.  
  
### <a name="xnodeequalitycomparer-class"></a>Klasa XNodeEqualityComparer  
 <xref:System.Xml.Linq.XNodeEqualityComparer>zapewnia funkcje do porównania węzły równości wartości.  
  
### <a name="xobject-class"></a>Klasa XObject  
 <xref:System.Xml.Linq.XObject>jest abstrakcyjna klasa podstawowa dla <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute>. Zawiera funkcję adnotacji i zdarzeń.  
  
### <a name="xobjectchange-class"></a>Klasa XObjectChange  
 <xref:System.Xml.Linq.XObjectChange>Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>Klasa XObjectChangeEventArgs  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.  
  
### <a name="xprocessinginstruction-class"></a>Klasa XProcessingInstruction  
 <xref:System.Xml.Linq.XProcessingInstruction>reprezentuje instrukcji przetwarzania XML. Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.  
  
### <a name="xtext-class"></a>Klasa XText  
 <xref:System.Xml.Linq.XText>reprezentuje węzeł tekstowy. W większości przypadków nie trzeba używać tej klasy. Ta klasa jest używana głównie dla zawartości mieszanej.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do programowania w języku XML-Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
