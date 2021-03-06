---
title: 'Vorgehensweise: Erstellen Sie eine HTML-Dokumentviewers in einer Windows Forms-Anwendung'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 83a29af28f5e58b75377805e443eb92cee39e272
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643701"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Vorgehensweise: Erstellen Sie eine HTML-Dokumentviewers in einer Windows Forms-Anwendung
Sie können die <xref:System.Windows.Forms.WebBrowser> Steuerelement zum Anzeigen und Drucken von HTML-Dokumente ohne den vollen Funktionsumfang von einem Internet-Web-Browser. Dies ist nützlich, wenn Sie die Formatierungsfunktionen von HTML nutzen möchten, aber möchten nicht, dass Ihre Benutzer, beliebige Webseiten zu laden, die nicht vertrauenswürdigen Websteuerelemente oder potenziell bösartige Skriptcode enthalten kann. Möglicherweise möchten Sie die Funktionalität des Einschränken der <xref:System.Windows.Forms.WebBrowser> Steuern auf diese Weise kann z. B. für die Verwendung als eine HTML-e-Mail-Viewer oder zum HTML-Hilfe in Ihrer Anwendung bereitstellen.  
  
### <a name="to-create-an-html-document-viewer"></a>Erstellen Sie eine HTML-Dokument-viewer  
  
1.  Festlegen der <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> Eigenschaft `false` um zu verhindern, dass die <xref:System.Windows.Forms.WebBrowser> -Steuerelement aus, Öffnen von Dateien, die auf ihm abgelegt werden.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Legen Sie die <xref:System.Windows.Forms.WebBrowser.Url%2A> -Eigenschaft auf die Position der ersten Datei angezeigt.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Ein <xref:System.Windows.Forms.WebBrowser>-Steuerelement namens `webBrowser1`.  
  
-   Verweise auf die Assemblys `System` und `System.Windows.Forms`.  
  
## <a name="see-also"></a>Siehe auch
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [Übersicht über das WebBrowser-Steuerelement](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
- [WebBrowser-Sicherheit](../../../../docs/framework/winforms/controls/webbrowser-security.md)
- [Vorgehensweise: Navigieren Sie zu einer URL mit dem WebBrowser-Steuerelement](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Vorgehensweise: Drucken Sie mit einem WebBrowser-Steuerelement](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
