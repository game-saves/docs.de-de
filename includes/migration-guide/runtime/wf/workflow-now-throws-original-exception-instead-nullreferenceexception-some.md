### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="78ae2-101">Der Workflow löst jetzt anstelle einer NullReferenceException teilweise eine ursprüngliche Ausnahme aus</span><span class="sxs-lookup"><span data-stu-id="78ae2-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="78ae2-102">Details</span><span class="sxs-lookup"><span data-stu-id="78ae2-102">Details</span></span>|<span data-ttu-id="78ae2-103">In .NET Framework 4.6.2 und früheren Versionen löst die System.Activities-Workflowruntime eine <code>null</code> aus, wenn die Execute-Methode einer Workflowaktivität eine Ausnahme mit einem <xref:System.Exception.Message>-Wert für die <xref:System.NullReferenceException?displayProperty=name>-Eigenschaft auslöst, wodurch die ursprüngliche Ausnahme maskiert wird. In .NET Framework 4.7 wird die zuvor maskierte Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="78ae2-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="78ae2-104">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="78ae2-104">Suggestion</span></span>|<span data-ttu-id="78ae2-105">Wenn Ihr Code von der Verarbeitung von <xref:System.NullReferenceException?displayProperty=name> abhängig ist, ändern Sie diesen, um die Ausnahmen zu erfassen, die Ihre benutzerdefinierten Aktivitäten auslösen könnten.</span><span class="sxs-lookup"><span data-stu-id="78ae2-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="78ae2-106">Bereich</span><span class="sxs-lookup"><span data-stu-id="78ae2-106">Scope</span></span>|<span data-ttu-id="78ae2-107">Gering</span><span class="sxs-lookup"><span data-stu-id="78ae2-107">Minor</span></span>|
|<span data-ttu-id="78ae2-108">Version</span><span class="sxs-lookup"><span data-stu-id="78ae2-108">Version</span></span>|<span data-ttu-id="78ae2-109">4.7</span><span class="sxs-lookup"><span data-stu-id="78ae2-109">4.7</span></span>|
|<span data-ttu-id="78ae2-110">Typ</span><span class="sxs-lookup"><span data-stu-id="78ae2-110">Type</span></span>|<span data-ttu-id="78ae2-111">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="78ae2-111">Runtime</span></span>|
|<span data-ttu-id="78ae2-112">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="78ae2-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
