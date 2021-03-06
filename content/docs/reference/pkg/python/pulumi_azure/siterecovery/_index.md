---
title: Module siterecovery
title_tag: Module siterecovery | Package pulumi_azure | Python SDK
linktitle: siterecovery
notitle: true
---

<div class="section" id="siterecovery">
<h1>siterecovery<a class="headerlink" href="#siterecovery" title="Permalink to this headline">¶</a></h1>
<blockquote>
<div><p>This provider is a derived work of the <a class="reference external" href="https://github.com/terraform-providers/terraform-provider-azurerm">Terraform Provider</a> distributed under
<a class="reference external" href="https://www.mozilla.org/en-US/MPL/2.0/">MPL 2.0</a>. If you encounter a bug or missing feature, first check the
<a class="reference external" href="https://github.com/pulumi/pulumi-azure/issues">pulumi/pulumi-azure repo</a>; however, if that doesn’t turn up
anything, please consult the source <a class="reference external" href="https://github.com/terraform-providers/terraform-provider-azurerm/issues">terraform-providers/terraform-provider-azurerm repo</a>.</p>
</div></blockquote>
<span class="target" id="module-pulumi_azure.siterecovery"></span><dl class="py class">
<dt id="pulumi_azure.siterecovery.Fabric">
<em class="property">class </em><code class="sig-prename descclassname">pulumi_azure.siterecovery.</code><code class="sig-name descname">Fabric</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">location</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__props__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__name__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__opts__</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric" title="Permalink to this definition">¶</a></dt>
<dd><p>Manages a Azure Site Recovery Replication Fabric within a Recovery Services vault. Only Azure fabrics are supported at this time. Replication Fabrics serve as a container within an Azure region for other Site Recovery resources such as protection containers, protected items, network mappings.</p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">pulumi</span>
<span class="kn">import</span> <span class="nn">pulumi_azure</span> <span class="k">as</span> <span class="nn">azure</span>

<span class="n">primary</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;primary&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;West US&quot;</span><span class="p">)</span>
<span class="n">secondary</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;secondary&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;East US&quot;</span><span class="p">)</span>
<span class="n">vault</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">recoveryservices</span><span class="o">.</span><span class="n">Vault</span><span class="p">(</span><span class="s2">&quot;vault&quot;</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">location</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">sku</span><span class="o">=</span><span class="s2">&quot;Standard&quot;</span><span class="p">)</span>
<span class="n">fabric</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">Fabric</span><span class="p">(</span><span class="s2">&quot;fabric&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">primary</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
</pre></div>
</div>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The name of the resource.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>location</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – In what region should the fabric be located.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.Fabric.location">
<code class="sig-name descname">location</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.location" title="Permalink to this definition">¶</a></dt>
<dd><p>In what region should the fabric be located.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.Fabric.name">
<code class="sig-name descname">name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the network mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.Fabric.recovery_vault_name">
<code class="sig-name descname">recovery_vault_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.recovery_vault_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the vault that should be updated.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.Fabric.resource_group_name">
<code class="sig-name descname">resource_group_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.resource_group_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the resource group where the vault that should be updated is located.</p>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.Fabric.get">
<em class="property">static </em><code class="sig-name descname">get</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">id</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">location</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.get" title="Permalink to this definition">¶</a></dt>
<dd><p>Get an existing Fabric resource’s state with the given name, id, and optional extra
properties used to qualify the lookup.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The unique name of the resulting resource.</p></li>
<li><p><strong>id</strong> (<em>str</em>) – The unique provider ID of the resource to lookup.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>location</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – In what region should the fabric be located.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.Fabric.translate_output_property">
<code class="sig-name descname">translate_output_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.translate_output_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of output properties
into a format of their choosing before writing those properties to the resource object.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.Fabric.translate_input_property">
<code class="sig-name descname">translate_input_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.Fabric.translate_input_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of input properties into
a format of their choosing before sending those properties to the Pulumi engine.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

</dd></dl>

<dl class="py class">
<dt id="pulumi_azure.siterecovery.NetworkMapping">
<em class="property">class </em><code class="sig-prename descclassname">pulumi_azure.siterecovery.</code><code class="sig-name descname">NetworkMapping</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_network_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_network_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__props__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__name__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__opts__</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping" title="Permalink to this definition">¶</a></dt>
<dd><p>Manages a site recovery network mapping on Azure. A network mapping decides how to translate connected netwroks when a VM is migrated from one region to another.</p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">pulumi</span>
<span class="kn">import</span> <span class="nn">pulumi_azure</span> <span class="k">as</span> <span class="nn">azure</span>

<span class="n">primary_resource_group</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;primaryResourceGroup&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;West US&quot;</span><span class="p">)</span>
<span class="n">secondary_resource_group</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;secondaryResourceGroup&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;East US&quot;</span><span class="p">)</span>
<span class="n">vault</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">recoveryservices</span><span class="o">.</span><span class="n">Vault</span><span class="p">(</span><span class="s2">&quot;vault&quot;</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">sku</span><span class="o">=</span><span class="s2">&quot;Standard&quot;</span><span class="p">)</span>
<span class="n">primary_fabric</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">Fabric</span><span class="p">(</span><span class="s2">&quot;primaryFabric&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">primary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="n">secondary_fabric</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">Fabric</span><span class="p">(</span><span class="s2">&quot;secondaryFabric&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="c1"># Avoids issues with crearing fabrics simultainusly</span>
<span class="n">primary_virtual_network</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">network</span><span class="o">.</span><span class="n">VirtualNetwork</span><span class="p">(</span><span class="s2">&quot;primaryVirtualNetwork&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">primary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">address_spaces</span><span class="o">=</span><span class="p">[</span><span class="s2">&quot;192.168.1.0/24&quot;</span><span class="p">],</span>
    <span class="n">location</span><span class="o">=</span><span class="n">primary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="n">secondary_virtual_network</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">network</span><span class="o">.</span><span class="n">VirtualNetwork</span><span class="p">(</span><span class="s2">&quot;secondaryVirtualNetwork&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">address_spaces</span><span class="o">=</span><span class="p">[</span><span class="s2">&quot;192.168.2.0/24&quot;</span><span class="p">],</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="n">recovery_mapping</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">NetworkMapping</span><span class="p">(</span><span class="s2">&quot;recovery-mapping&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">source_recovery_fabric_name</span><span class="o">=</span><span class="s2">&quot;primary-fabric&quot;</span><span class="p">,</span>
    <span class="n">target_recovery_fabric_name</span><span class="o">=</span><span class="s2">&quot;secondary-fabric&quot;</span><span class="p">,</span>
    <span class="n">source_network_id</span><span class="o">=</span><span class="n">primary_virtual_network</span><span class="o">.</span><span class="n">id</span><span class="p">,</span>
    <span class="n">target_network_id</span><span class="o">=</span><span class="n">secondary_virtual_network</span><span class="o">.</span><span class="n">id</span><span class="p">)</span>
</pre></div>
</div>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The name of the resource.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
<li><p><strong>source_network_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The id of the primary network.</p></li>
<li><p><strong>source_recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Specifies the ASR fabric where mapping should be created.</p></li>
<li><p><strong>target_network_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The id of the recovery network.</p></li>
<li><p><strong>target_recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The Azure Site Recovery fabric object corresponding to the recovery Azure region.</p></li>
</ul>
</dd>
</dl>
<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.name">
<code class="sig-name descname">name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the network mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.recovery_vault_name">
<code class="sig-name descname">recovery_vault_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.recovery_vault_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the vault that should be updated.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.resource_group_name">
<code class="sig-name descname">resource_group_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.resource_group_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the resource group where the vault that should be updated is located.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.source_network_id">
<code class="sig-name descname">source_network_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.source_network_id" title="Permalink to this definition">¶</a></dt>
<dd><p>The id of the primary network.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.source_recovery_fabric_name">
<code class="sig-name descname">source_recovery_fabric_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.source_recovery_fabric_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Specifies the ASR fabric where mapping should be created.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.target_network_id">
<code class="sig-name descname">target_network_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.target_network_id" title="Permalink to this definition">¶</a></dt>
<dd><p>The id of the recovery network.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.NetworkMapping.target_recovery_fabric_name">
<code class="sig-name descname">target_recovery_fabric_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.target_recovery_fabric_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The Azure Site Recovery fabric object corresponding to the recovery Azure region.</p>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.NetworkMapping.get">
<em class="property">static </em><code class="sig-name descname">get</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">id</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_network_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_network_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.get" title="Permalink to this definition">¶</a></dt>
<dd><p>Get an existing NetworkMapping resource’s state with the given name, id, and optional extra
properties used to qualify the lookup.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The unique name of the resulting resource.</p></li>
<li><p><strong>id</strong> (<em>str</em>) – The unique provider ID of the resource to lookup.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
<li><p><strong>source_network_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The id of the primary network.</p></li>
<li><p><strong>source_recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Specifies the ASR fabric where mapping should be created.</p></li>
<li><p><strong>target_network_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The id of the recovery network.</p></li>
<li><p><strong>target_recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The Azure Site Recovery fabric object corresponding to the recovery Azure region.</p></li>
</ul>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.NetworkMapping.translate_output_property">
<code class="sig-name descname">translate_output_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.translate_output_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of output properties
into a format of their choosing before writing those properties to the resource object.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.NetworkMapping.translate_input_property">
<code class="sig-name descname">translate_input_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.NetworkMapping.translate_input_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of input properties into
a format of their choosing before sending those properties to the Pulumi engine.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

</dd></dl>

<dl class="py class">
<dt id="pulumi_azure.siterecovery.ProtectionContainer">
<em class="property">class </em><code class="sig-prename descclassname">pulumi_azure.siterecovery.</code><code class="sig-name descname">ProtectionContainer</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__props__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__name__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__opts__</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer" title="Permalink to this definition">¶</a></dt>
<dd><p>Manages a Azure Site Recovery protection container. Protection containers serve as containers for replicated VMs and belong to a single region / recovery fabric. Protection containers can contain more than one replicated VM. To replicate a VM, a container must exist in both the source and target Azure regions.</p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">pulumi</span>
<span class="kn">import</span> <span class="nn">pulumi_azure</span> <span class="k">as</span> <span class="nn">azure</span>

<span class="n">primary</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;primary&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;West US&quot;</span><span class="p">)</span>
<span class="n">secondary</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;secondary&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;East US&quot;</span><span class="p">)</span>
<span class="n">vault</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">recoveryservices</span><span class="o">.</span><span class="n">Vault</span><span class="p">(</span><span class="s2">&quot;vault&quot;</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">location</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">sku</span><span class="o">=</span><span class="s2">&quot;Standard&quot;</span><span class="p">)</span>
<span class="n">fabric</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">Fabric</span><span class="p">(</span><span class="s2">&quot;fabric&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">primary</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="n">protection_container</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">ProtectionContainer</span><span class="p">(</span><span class="s2">&quot;protection-container&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_fabric_name</span><span class="o">=</span><span class="n">fabric</span><span class="o">.</span><span class="n">name</span><span class="p">)</span>
</pre></div>
</div>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The name of the resource.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of fabric that should contain this protection container.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.name">
<code class="sig-name descname">name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the network mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.recovery_fabric_name">
<code class="sig-name descname">recovery_fabric_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.recovery_fabric_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of fabric that should contain this protection container.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.recovery_vault_name">
<code class="sig-name descname">recovery_vault_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.recovery_vault_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the vault that should be updated.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.resource_group_name">
<code class="sig-name descname">resource_group_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.resource_group_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the resource group where the vault that should be updated is located.</p>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.get">
<em class="property">static </em><code class="sig-name descname">get</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">id</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.get" title="Permalink to this definition">¶</a></dt>
<dd><p>Get an existing ProtectionContainer resource’s state with the given name, id, and optional extra
properties used to qualify the lookup.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The unique name of the resulting resource.</p></li>
<li><p><strong>id</strong> (<em>str</em>) – The unique provider ID of the resource to lookup.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of fabric that should contain this protection container.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.translate_output_property">
<code class="sig-name descname">translate_output_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.translate_output_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of output properties
into a format of their choosing before writing those properties to the resource object.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ProtectionContainer.translate_input_property">
<code class="sig-name descname">translate_input_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainer.translate_input_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of input properties into
a format of their choosing before sending those properties to the Pulumi engine.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

</dd></dl>

<dl class="py class">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping">
<em class="property">class </em><code class="sig-prename descclassname">pulumi_azure.siterecovery.</code><code class="sig-name descname">ProtectionContainerMapping</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_replication_policy_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_source_protection_container_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_target_protection_container_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__props__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__name__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__opts__</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping" title="Permalink to this definition">¶</a></dt>
<dd><p>Manages a Azure recovery vault protection container mapping. A protection container mapping decides how to translate the protection container when a VM is migrated from one region to another.</p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">pulumi</span>
<span class="kn">import</span> <span class="nn">pulumi_azure</span> <span class="k">as</span> <span class="nn">azure</span>

<span class="n">primary_resource_group</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;primaryResourceGroup&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;West US&quot;</span><span class="p">)</span>
<span class="n">secondary_resource_group</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;secondaryResourceGroup&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;East US&quot;</span><span class="p">)</span>
<span class="n">vault</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">recoveryservices</span><span class="o">.</span><span class="n">Vault</span><span class="p">(</span><span class="s2">&quot;vault&quot;</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">sku</span><span class="o">=</span><span class="s2">&quot;Standard&quot;</span><span class="p">)</span>
<span class="n">primary_fabric</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">Fabric</span><span class="p">(</span><span class="s2">&quot;primaryFabric&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">primary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="n">secondary_fabric</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">Fabric</span><span class="p">(</span><span class="s2">&quot;secondaryFabric&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">location</span><span class="p">)</span>
<span class="n">primary_protection_container</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">ProtectionContainer</span><span class="p">(</span><span class="s2">&quot;primaryProtectionContainer&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_fabric_name</span><span class="o">=</span><span class="n">primary_fabric</span><span class="o">.</span><span class="n">name</span><span class="p">)</span>
<span class="n">secondary_protection_container</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">ProtectionContainer</span><span class="p">(</span><span class="s2">&quot;secondaryProtectionContainer&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_fabric_name</span><span class="o">=</span><span class="n">secondary_fabric</span><span class="o">.</span><span class="n">name</span><span class="p">)</span>
<span class="n">policy</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">ReplicationPolicy</span><span class="p">(</span><span class="s2">&quot;policy&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_point_retention_in_minutes</span><span class="o">=</span><span class="mi">24</span> <span class="o">*</span> <span class="mi">60</span><span class="p">,</span>
    <span class="n">application_consistent_snapshot_frequency_in_minutes</span><span class="o">=</span><span class="mi">4</span> <span class="o">*</span> <span class="mi">60</span><span class="p">)</span>
<span class="n">container_mapping</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">ProtectionContainerMapping</span><span class="p">(</span><span class="s2">&quot;container-mapping&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary_resource_group</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_fabric_name</span><span class="o">=</span><span class="n">primary_fabric</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_source_protection_container_name</span><span class="o">=</span><span class="n">primary_protection_container</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_target_protection_container_id</span><span class="o">=</span><span class="n">secondary_protection_container</span><span class="o">.</span><span class="n">id</span><span class="p">,</span>
    <span class="n">recovery_replication_policy_id</span><span class="o">=</span><span class="n">policy</span><span class="o">.</span><span class="n">id</span><span class="p">)</span>
</pre></div>
</div>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The name of the resource.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of fabric that should contains the protection container to map.</p></li>
<li><p><strong>recovery_replication_policy_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of the policy to use for this mapping.</p></li>
<li><p><strong>recovery_source_protection_container_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the source protection container to map.</p></li>
<li><p><strong>recovery_target_protection_container_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of target protection container to map to.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.name">
<code class="sig-name descname">name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the network mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_fabric_name">
<code class="sig-name descname">recovery_fabric_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_fabric_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of fabric that should contains the protection container to map.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_replication_policy_id">
<code class="sig-name descname">recovery_replication_policy_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_replication_policy_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of the policy to use for this mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_source_protection_container_name">
<code class="sig-name descname">recovery_source_protection_container_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_source_protection_container_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the source protection container to map.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_target_protection_container_id">
<code class="sig-name descname">recovery_target_protection_container_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_target_protection_container_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of target protection container to map to.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_vault_name">
<code class="sig-name descname">recovery_vault_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.recovery_vault_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the vault that should be updated.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.resource_group_name">
<code class="sig-name descname">resource_group_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.resource_group_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the resource group where the vault that should be updated is located.</p>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.get">
<em class="property">static </em><code class="sig-name descname">get</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">id</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_replication_policy_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_source_protection_container_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_target_protection_container_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.get" title="Permalink to this definition">¶</a></dt>
<dd><p>Get an existing ProtectionContainerMapping resource’s state with the given name, id, and optional extra
properties used to qualify the lookup.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The unique name of the resulting resource.</p></li>
<li><p><strong>id</strong> (<em>str</em>) – The unique provider ID of the resource to lookup.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of fabric that should contains the protection container to map.</p></li>
<li><p><strong>recovery_replication_policy_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of the policy to use for this mapping.</p></li>
<li><p><strong>recovery_source_protection_container_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the source protection container to map.</p></li>
<li><p><strong>recovery_target_protection_container_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of target protection container to map to.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.translate_output_property">
<code class="sig-name descname">translate_output_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.translate_output_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of output properties
into a format of their choosing before writing those properties to the resource object.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ProtectionContainerMapping.translate_input_property">
<code class="sig-name descname">translate_input_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ProtectionContainerMapping.translate_input_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of input properties into
a format of their choosing before sending those properties to the Pulumi engine.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

</dd></dl>

<dl class="py class">
<dt id="pulumi_azure.siterecovery.ReplicatedVM">
<em class="property">class </em><code class="sig-prename descclassname">pulumi_azure.siterecovery.</code><code class="sig-name descname">ReplicatedVM</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">managed_disks</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_replication_policy_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_recovery_protection_container_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_vm_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_availability_set_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_recovery_fabric_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_recovery_protection_container_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_resource_group_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__props__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__name__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__opts__</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM" title="Permalink to this definition">¶</a></dt>
<dd><p>Manages a VM replicated using Azure Site Recovery (Azure to Azure only). A replicated VM keeps a copiously updated image of the VM in another region in order to be able to start the VM in that region in case of a disaster.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The name of the resource.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>managed_disks</strong> (<em>pulumi.Input</em><em>[</em><em>list</em><em>]</em>) – One or more <code class="docutils literal notranslate"><span class="pre">managed_disk</span></code> block.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
<li><p><strong>source_recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of fabric that should contains this replication.</p></li>
<li><p><strong>source_recovery_protection_container_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the protection container to use.</p></li>
<li><p><strong>source_vm_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of the VM to replicate</p></li>
<li><p><strong>target_availability_set_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of availability set that the new VM should belong to when a failover is done.</p></li>
<li><p><strong>target_recovery_fabric_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of fabric where the VM replication should be handled when a failover is done.</p></li>
<li><p><strong>target_recovery_protection_container_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of protection container where the VM replication should be created when a failover is done.</p></li>
<li><p><strong>target_resource_group_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of resource group where the VM should be created when a failover is done.</p></li>
</ul>
</dd>
</dl>
<p>The <strong>managed_disks</strong> object supports the following:</p>
<ul class="simple">
<li><p><code class="docutils literal notranslate"><span class="pre">diskId</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - Id of disk that should be replicated.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">stagingStorageAccountId</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - Storage account that should be used for caching.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">targetDiskType</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - What type should the disk be when a failover is done.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">targetReplicaDiskType</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - What type should the disk be that holds the replication data.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">target_resource_group_id</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - Resource group disk should belong to when a failover is done.</p></li>
</ul>
<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.managed_disks">
<code class="sig-name descname">managed_disks</code><em class="property">: pulumi.Output[list]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.managed_disks" title="Permalink to this definition">¶</a></dt>
<dd><p>One or more <code class="docutils literal notranslate"><span class="pre">managed_disk</span></code> block.</p>
<ul class="simple">
<li><p><code class="docutils literal notranslate"><span class="pre">diskId</span></code> (<code class="docutils literal notranslate"><span class="pre">str</span></code>) - Id of disk that should be replicated.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">stagingStorageAccountId</span></code> (<code class="docutils literal notranslate"><span class="pre">str</span></code>) - Storage account that should be used for caching.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">targetDiskType</span></code> (<code class="docutils literal notranslate"><span class="pre">str</span></code>) - What type should the disk be when a failover is done.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">targetReplicaDiskType</span></code> (<code class="docutils literal notranslate"><span class="pre">str</span></code>) - What type should the disk be that holds the replication data.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">target_resource_group_id</span></code> (<code class="docutils literal notranslate"><span class="pre">str</span></code>) - Resource group disk should belong to when a failover is done.</p></li>
</ul>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.name">
<code class="sig-name descname">name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the network mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.recovery_vault_name">
<code class="sig-name descname">recovery_vault_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.recovery_vault_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the vault that should be updated.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.resource_group_name">
<code class="sig-name descname">resource_group_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.resource_group_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the resource group where the vault that should be updated is located.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.source_recovery_fabric_name">
<code class="sig-name descname">source_recovery_fabric_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.source_recovery_fabric_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of fabric that should contains this replication.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.source_recovery_protection_container_name">
<code class="sig-name descname">source_recovery_protection_container_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.source_recovery_protection_container_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the protection container to use.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.source_vm_id">
<code class="sig-name descname">source_vm_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.source_vm_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of the VM to replicate</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.target_availability_set_id">
<code class="sig-name descname">target_availability_set_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.target_availability_set_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of availability set that the new VM should belong to when a failover is done.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.target_recovery_fabric_id">
<code class="sig-name descname">target_recovery_fabric_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.target_recovery_fabric_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of fabric where the VM replication should be handled when a failover is done.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.target_recovery_protection_container_id">
<code class="sig-name descname">target_recovery_protection_container_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.target_recovery_protection_container_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of protection container where the VM replication should be created when a failover is done.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.target_resource_group_id">
<code class="sig-name descname">target_resource_group_id</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.target_resource_group_id" title="Permalink to this definition">¶</a></dt>
<dd><p>Id of resource group where the VM should be created when a failover is done.</p>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.get">
<em class="property">static </em><code class="sig-name descname">get</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">id</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">managed_disks</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_replication_policy_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_recovery_fabric_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_recovery_protection_container_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">source_vm_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_availability_set_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_recovery_fabric_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_recovery_protection_container_id</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">target_resource_group_id</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.get" title="Permalink to this definition">¶</a></dt>
<dd><p>Get an existing ReplicatedVM resource’s state with the given name, id, and optional extra
properties used to qualify the lookup.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The unique name of the resulting resource.</p></li>
<li><p><strong>id</strong> (<em>str</em>) – The unique provider ID of the resource to lookup.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>managed_disks</strong> (<em>pulumi.Input</em><em>[</em><em>list</em><em>]</em>) – One or more <code class="docutils literal notranslate"><span class="pre">managed_disk</span></code> block.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
<li><p><strong>source_recovery_fabric_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of fabric that should contains this replication.</p></li>
<li><p><strong>source_recovery_protection_container_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the protection container to use.</p></li>
<li><p><strong>source_vm_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of the VM to replicate</p></li>
<li><p><strong>target_availability_set_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of availability set that the new VM should belong to when a failover is done.</p></li>
<li><p><strong>target_recovery_fabric_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of fabric where the VM replication should be handled when a failover is done.</p></li>
<li><p><strong>target_recovery_protection_container_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of protection container where the VM replication should be created when a failover is done.</p></li>
<li><p><strong>target_resource_group_id</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Id of resource group where the VM should be created when a failover is done.</p></li>
</ul>
</dd>
</dl>
<p>The <strong>managed_disks</strong> object supports the following:</p>
<ul class="simple">
<li><p><code class="docutils literal notranslate"><span class="pre">diskId</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - Id of disk that should be replicated.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">stagingStorageAccountId</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - Storage account that should be used for caching.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">targetDiskType</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - What type should the disk be when a failover is done.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">targetReplicaDiskType</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - What type should the disk be that holds the replication data.</p></li>
<li><p><code class="docutils literal notranslate"><span class="pre">target_resource_group_id</span></code> (<code class="docutils literal notranslate"><span class="pre">pulumi.Input[str]</span></code>) - Resource group disk should belong to when a failover is done.</p></li>
</ul>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.translate_output_property">
<code class="sig-name descname">translate_output_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.translate_output_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of output properties
into a format of their choosing before writing those properties to the resource object.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ReplicatedVM.translate_input_property">
<code class="sig-name descname">translate_input_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicatedVM.translate_input_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of input properties into
a format of their choosing before sending those properties to the Pulumi engine.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

</dd></dl>

<dl class="py class">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy">
<em class="property">class </em><code class="sig-prename descclassname">pulumi_azure.siterecovery.</code><code class="sig-name descname">ReplicationPolicy</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">application_consistent_snapshot_frequency_in_minutes</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_point_retention_in_minutes</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__props__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__name__</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">__opts__</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy" title="Permalink to this definition">¶</a></dt>
<dd><p>Manages a Azure Site Recovery replication policy within a recovery vault. Replication policies define the frequency at which recovery points are created and how long they are stored.</p>
<div class="highlight-python notranslate"><div class="highlight"><pre><span></span><span class="kn">import</span> <span class="nn">pulumi</span>
<span class="kn">import</span> <span class="nn">pulumi_azure</span> <span class="k">as</span> <span class="nn">azure</span>

<span class="n">secondary</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">core</span><span class="o">.</span><span class="n">ResourceGroup</span><span class="p">(</span><span class="s2">&quot;secondary&quot;</span><span class="p">,</span> <span class="n">location</span><span class="o">=</span><span class="s2">&quot;East US&quot;</span><span class="p">)</span>
<span class="n">vault</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">recoveryservices</span><span class="o">.</span><span class="n">Vault</span><span class="p">(</span><span class="s2">&quot;vault&quot;</span><span class="p">,</span>
    <span class="n">location</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">location</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">sku</span><span class="o">=</span><span class="s2">&quot;Standard&quot;</span><span class="p">)</span>
<span class="n">policy</span> <span class="o">=</span> <span class="n">azure</span><span class="o">.</span><span class="n">siterecovery</span><span class="o">.</span><span class="n">ReplicationPolicy</span><span class="p">(</span><span class="s2">&quot;policy&quot;</span><span class="p">,</span>
    <span class="n">resource_group_name</span><span class="o">=</span><span class="n">secondary</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_vault_name</span><span class="o">=</span><span class="n">vault</span><span class="o">.</span><span class="n">name</span><span class="p">,</span>
    <span class="n">recovery_point_retention_in_minutes</span><span class="o">=</span><span class="mi">24</span> <span class="o">*</span> <span class="mi">60</span><span class="p">,</span>
    <span class="n">application_consistent_snapshot_frequency_in_minutes</span><span class="o">=</span><span class="mi">4</span> <span class="o">*</span> <span class="mi">60</span><span class="p">)</span>
</pre></div>
</div>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The name of the resource.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>application_consistent_snapshot_frequency_in_minutes</strong> (<em>pulumi.Input</em><em>[</em><em>float</em><em>]</em>) – Specifies the frequency(in minutes) at which to create application consistent recovery points.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_point_retention_in_minutes</strong> (<em>pulumi.Input</em><em>[</em><em>float</em><em>]</em>) – The duration in minutes for which the recovery points need to be stored.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.application_consistent_snapshot_frequency_in_minutes">
<code class="sig-name descname">application_consistent_snapshot_frequency_in_minutes</code><em class="property">: pulumi.Output[float]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.application_consistent_snapshot_frequency_in_minutes" title="Permalink to this definition">¶</a></dt>
<dd><p>Specifies the frequency(in minutes) at which to create application consistent recovery points.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.name">
<code class="sig-name descname">name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the network mapping.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.recovery_point_retention_in_minutes">
<code class="sig-name descname">recovery_point_retention_in_minutes</code><em class="property">: pulumi.Output[float]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.recovery_point_retention_in_minutes" title="Permalink to this definition">¶</a></dt>
<dd><p>The duration in minutes for which the recovery points need to be stored.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.recovery_vault_name">
<code class="sig-name descname">recovery_vault_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.recovery_vault_name" title="Permalink to this definition">¶</a></dt>
<dd><p>The name of the vault that should be updated.</p>
</dd></dl>

<dl class="py attribute">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.resource_group_name">
<code class="sig-name descname">resource_group_name</code><em class="property">: pulumi.Output[str]</em><em class="property"> = None</em><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.resource_group_name" title="Permalink to this definition">¶</a></dt>
<dd><p>Name of the resource group where the vault that should be updated is located.</p>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.get">
<em class="property">static </em><code class="sig-name descname">get</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">resource_name</span></em>, <em class="sig-param"><span class="n">id</span></em>, <em class="sig-param"><span class="n">opts</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">application_consistent_snapshot_frequency_in_minutes</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_point_retention_in_minutes</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">recovery_vault_name</span><span class="o">=</span><span class="default_value">None</span></em>, <em class="sig-param"><span class="n">resource_group_name</span><span class="o">=</span><span class="default_value">None</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.get" title="Permalink to this definition">¶</a></dt>
<dd><p>Get an existing ReplicationPolicy resource’s state with the given name, id, and optional extra
properties used to qualify the lookup.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><ul class="simple">
<li><p><strong>resource_name</strong> (<em>str</em>) – The unique name of the resulting resource.</p></li>
<li><p><strong>id</strong> (<em>str</em>) – The unique provider ID of the resource to lookup.</p></li>
<li><p><strong>opts</strong> (<a class="reference internal" href="../../pulumi/#pulumi.ResourceOptions" title="pulumi.ResourceOptions"><em>pulumi.ResourceOptions</em></a>) – Options for the resource.</p></li>
<li><p><strong>application_consistent_snapshot_frequency_in_minutes</strong> (<em>pulumi.Input</em><em>[</em><em>float</em><em>]</em>) – Specifies the frequency(in minutes) at which to create application consistent recovery points.</p></li>
<li><p><strong>name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the network mapping.</p></li>
<li><p><strong>recovery_point_retention_in_minutes</strong> (<em>pulumi.Input</em><em>[</em><em>float</em><em>]</em>) – The duration in minutes for which the recovery points need to be stored.</p></li>
<li><p><strong>recovery_vault_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – The name of the vault that should be updated.</p></li>
<li><p><strong>resource_group_name</strong> (<em>pulumi.Input</em><em>[</em><em>str</em><em>]</em>) – Name of the resource group where the vault that should be updated is located.</p></li>
</ul>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.translate_output_property">
<code class="sig-name descname">translate_output_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.translate_output_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of output properties
into a format of their choosing before writing those properties to the resource object.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

<dl class="py method">
<dt id="pulumi_azure.siterecovery.ReplicationPolicy.translate_input_property">
<code class="sig-name descname">translate_input_property</code><span class="sig-paren">(</span><em class="sig-param"><span class="n">prop</span></em><span class="sig-paren">)</span><a class="headerlink" href="#pulumi_azure.siterecovery.ReplicationPolicy.translate_input_property" title="Permalink to this definition">¶</a></dt>
<dd><p>Provides subclasses of Resource an opportunity to translate names of input properties into
a format of their choosing before sending those properties to the Pulumi engine.</p>
<dl class="field-list simple">
<dt class="field-odd">Parameters</dt>
<dd class="field-odd"><p><strong>prop</strong> (<em>str</em>) – A property name.</p>
</dd>
<dt class="field-even">Returns</dt>
<dd class="field-even"><p>A potentially transformed property name.</p>
</dd>
<dt class="field-odd">Return type</dt>
<dd class="field-odd"><p>str</p>
</dd>
</dl>
</dd></dl>

</dd></dl>

</div>
