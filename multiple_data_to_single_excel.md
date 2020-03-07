code

install.packages("sas7bdat")
install.packages("openxlsx")
install.packages("rJava")
library(sas7bdat)
library(openxlsx)

setwd("F:/Google/Allergy_KMG/Research/Montelukast_suicidal")

rm(list=ls())

cder_mpl2p_wp014 <- createWorkbook()

src_dir <- c("F:/Google/Allergy_KMG/Research/Montelukast_suicidal/sentinel-analytic-packages-cder_mpl2p_wp014@0b383f8268e/inputfiles")
src_file <- list.files(src_dir)
src_file_cnt <- length(src_file)

for(i in 1:src_file_cnt) {
  dataset <- read.sas7bdat(paste(src_dir, "/", src_file[i], sep=""))
  addWorksheet(cder_mpl2p_wp014, src_file[i])
  print(head(dataset))
  writeDataTable(cder_mpl2p_wp014, src_file[i], dataset)
}

saveWorkbook(cder_mpl2p_wp014, file="cder_mpl2p_wp014.xlsx")

cder_mpl2p_wp010 <- createWorkbook()

src_dir <- c("F:/Google/Allergy_KMG/Research/Montelukast_suicidal/sentinel-analytic-packages-cder_mpl2r_wp010@b3d11fb4363/inputfiles")
src_file <- list.files(src_dir)
src_file_cnt <- length(src_file)

for(i in 1:src_file_cnt) {
  dataset <- read.sas7bdat(paste(src_dir, "/", src_file[i], sep=""))
  addWorksheet(cder_mpl2p_wp010, src_file[i])
  print(head(dataset))
  writeDataTable(cder_mpl2p_wp010, src_file[i], dataset)
}

saveWorkbook(cder_mpl2p_wp010, file="cder_mpl2p_wp010.xlsx")
