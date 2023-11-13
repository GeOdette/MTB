BiocManager::install("VariantAnnotation")
library(dplyr)
library(ggplot2)
variants_df<-read.csv('/home/odette/MTB_ANAL/vcf/annotated_vcfs/ERR3077930_filteredAnnotations.csv', header = TRUE, sep = '\t')
head(variants_df)
variant_frequency <- variants_df %>% select(ANN....GENE, ANN....EFFECT, ANN....IMPACT, ANN....FEATUREID, ANN....CODON) %>% group_by(ANN....GENE, ANN....CODON, ANN....IMPACT, ANN....EFFECT) %>% summarise(Frequency = n())
common_variants <- variant_frequency %>% filter(ANN....IMPACT == "HIGH")
str(variants_df)

common_variants %>% ggplot(aes(y= ANN....GENE)) +
  geom_bar() +
  xlab("Frequency") +
  ylab("Variants")

megred_df<- read.csv('from_merged_vcf.csv', sep = '\t')
frequency_df <-megred_df %>% group_by(ANN....HGVS_C) %>% summarise(Frequency = n()) %>%
  arrange(desc(Frequency))
