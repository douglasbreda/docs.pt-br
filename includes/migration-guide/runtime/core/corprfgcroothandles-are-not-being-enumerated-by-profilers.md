### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="e4221-101">COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil</span><span class="sxs-lookup"><span data-stu-id="e4221-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e4221-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e4221-102">Details</span></span>|<span data-ttu-id="e4221-103">No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>).</span><span class="sxs-lookup"><span data-stu-id="e4221-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="e4221-104">Esse problema foi corrigido a partir do .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="e4221-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="e4221-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e4221-105">Suggestion</span></span>|<span data-ttu-id="e4221-106">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4221-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="e4221-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="e4221-107">Scope</span></span>|<span data-ttu-id="e4221-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="e4221-108">Minor</span></span>|
|<span data-ttu-id="e4221-109">Versão</span><span class="sxs-lookup"><span data-stu-id="e4221-109">Version</span></span>|<span data-ttu-id="e4221-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e4221-110">4.5.1</span></span>|
|<span data-ttu-id="e4221-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="e4221-111">Type</span></span>|<span data-ttu-id="e4221-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e4221-112">Runtime</span></span>|
