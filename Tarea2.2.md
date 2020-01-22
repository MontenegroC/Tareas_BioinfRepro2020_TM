#QC – Plink#



En este caso antes de comenzar el control de calidad, fue necesario crear archivos **.ped** y **.map.**

**Comando utilizado:**

``
plink --vcf batch_1.vcf --allow-extra-chr --recode --out tami
``

**Donde:**

**Bach_1.vcf** es el archivo madre.

##Paso 1: Filtros##

**1.	Missingness of SNPs:**
Excluye los SNP que faltan en una gran proporción de los individuos. En este paso, se eliminan los SNP con llamadas de bajo genotipo.


**2.	Missingness individuals:**
Excluye a los individuos que tienen altas tasas de perdida de genotipo. En este paso, se eliminan los sujetos con llamadas de bajo genotipo.

Se recomienda filtrar en una primera estapa tanto SNPs como individuos con un umbral relajado de 0.2 o mayor a 20%, ya que de esta manera se filtraran los que posean perdida muy alta. Luego de esto de ser necesario se puede aplicar un filtro mas estricto (0.02).

Es importante realizar primero el filtrado de SNP y luego el filtrado de individuos.

**Comando:**

```
Missingness of SNPs -> $ --geno

Missingness individuals -> $ --mind
```

**Ejemplo:**

```
plink 
--file tami 
--geno 0.2 
--mind 0.2 
--make-bed 
--allow-extra-chr 
--out tami_geno0.2_mind0.2
```

