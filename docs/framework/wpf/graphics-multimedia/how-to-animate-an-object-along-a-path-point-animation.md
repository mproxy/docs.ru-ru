---
title: "Практическое руководство. Анимация объекта вдоль пути (точечная анимация)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399d6b8028b8715f38335089a723707657df4a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Практическое руководство. Анимация объекта вдоль пути (точечная анимация)
В этом примере показано, как использовать <xref:System.Windows.Media.Animation.PointAnimationUsingPath> анимируемый объект <xref:System.Windows.Point> вдоль пути кривой.  
  
## <a name="example"></a>Пример  
 В следующем примере перемещается <xref:System.Windows.Media.EllipseGeometry> вдоль пути, заданного с <xref:System.Windows.Media.PathGeometry>. Эллипс <xref:System.Windows.Media.EllipseGeometry.Center%2A> свойства, которое принимает <xref:System.Windows.Point> значений, определяет его положение; Чтобы переместить эллипс, анимация вы его <xref:System.Windows.Media.EllipseGeometry.Center%2A> свойство. В этом примере <xref:System.Windows.Media.Animation.PointAnimationUsingPath> для анимации <xref:System.Windows.Media.EllipseGeometry> объекта <xref:System.Windows.Media.EllipseGeometry.Center%2A> свойство.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Полный пример см. в разделе [Пример анимации пути](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 В версии кода в предыдущем примере используется <xref:System.Windows.Media.Animation.Storyboard> для анимации <xref:System.Windows.Media.EllipseGeometry>, несмотря на то, что была применена только одна анимация. Объект <xref:System.Windows.Media.Animation.Storyboard> часто является самым простым способом применения нескольких эффектов анимации, так как эти анимации можно управлять одним и тем же <xref:System.Windows.Media.Animation.Storyboard>. Однако, более простой способ применить одну анимацию к свойству при использовании кода является использование <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> метода. Пример см. в разделе [Анимация свойства без использования раскадровки](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>См. также  
 [Пример анимации вдоль пути](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Общие сведения об эффектах анимации](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Практические руководства, посвященные анимации по контуру](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
