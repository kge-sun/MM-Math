
<p align="center">
    🤗 <a href="https://huggingface.co/datasets/THUDM/LongBench" target="_blank">HF Repo</a> • 📃 <a href="https://arxiv.org/abs/2308.14508" target="_blank">Paper</a>
</p>





# 📖 MM-MATH: Advancing Multimodal Math Evaluation with Process Evaluation and Fine-grained Classification
**MM-Math** is a benchmark designed to evaluate the mathematical reasoning capabilities of multimodal models, featuring problems that incorporate images and step-by-step reasoning. All problems are calculation-based and utilize an **open-ended** format. MM-MATH is annotated across three dimensions: difficulty, grade level, and knowledge points, enabling comprehensive evaluation of multimodal models. 


We recognize the potentially high costs associated with model evaluation, particularly in scenarios involving diagrammatic math reasoning. Consequently, we adopt two fully automated evaluation method: outcome evaluation and process evaluation. For outcome evaluation, the final answer in MM-MATH is enclosed in \boxed{} format, requiring the extraction of models' final answer in the same format. For process evaluation, we provide carefully designed prompts, using GPT-4V to compare the model's problem-solving process with the ground truth, identify the first error, and classify it.



<!-- 
## 🔍 Table of Contents
- [🖥️ Leaderboard](#leaderboard)
- [⚙️ How to evaluate on LongBench](#how-to-evaluate-on-LongBench)
- [📊 Evaluation Result on Each Dataset](#evaluation-result-on-each-dataset)
- [📄 Acknowledgement](#acknowledgement)
- [📝 Citation](#citation) -->
  
<a name="leaderboard"></a>
## 🖥️ Leaderboard
 Here is the average scores (%) on the outcome evaluation under the Zero-shot scenario. We conducted assessments across three dimensions: difficulty, grade level, and knowledge points. Human evaluation results are derived from exam scores.

#### Multimodal Modal w/o Image
| Model                | Easy | Medium | Hard | Seven | Eight | Nine | Trans | Shape | Func | Average |
|-------------------------------|---------------|-----------------|---------------|----------------|----------------|---------------|----------------|----------------|---------------|------------------|
| Human                | 90.7          | 81.9            | 47.6          | 85.6           | 73.7           | 77.9          | 81.1           | 83.2           | 77.5          | 80.4             |
| Gemini-Pro-V         | 10.1          | 5.7             | 1.8           | 10.0           | 5.3            | 6.7           | 6.6            | 5.7            | 6.4           | 6.2              |
| Claude-3-Opus        | 31.7          | 17.3            | 7.2           | 32.5           | 14.9           | 2.2           | 20.8           | 18.5           | 12.9          | 19.2             |
| GPT-4                | 37.0          | 20.3            | 7.2           | 38.7           | 17.1           | 26.2          | 23.3           | 21.4           | 18.1          | 22.5             |
| GPT-4V               | 35.2          | 18.1            | 7.2           | 31.2           | 17.2           | 22.3          | 18.4           | 21.4           | 13.3          | 20.4             |
| GPT-4o               | 41.4          | 23.9            | 3.6           | 35.0           | 23.9           | 30.5          | 22.8           | 29.7           | 19.4          | 27.6             |
#### Multimodal modal w/ Image
| Model                | Easy | Medium | Hard | Seven | Eight | Nine | Trans | Shape | Func | Average |
|-------------------------------|---------------|-----------------|---------------|----------------|----------------|---------------|----------------|----------------|---------------|------------------|
| Human                | 90.7          | 81.9            | 47.6          | 85.6           | 73.7           | 77.9          | 81.1           | 83.2           | 77.5          | 80.4    
| DeepSeek-VL-7B-Chat  | 17.4          | 4.7             | 1.4           | 7.5            | 6.6            | 3.9           | 3.4            | 6.0            | 3.5           | 5.4              |
| Yi-34B-Chat          | 12.9          | 5.0             | 1.5           | 21.3           | 5.6            | 3.5           | 5.0            | 7.6            | 3.8           | 6.5              |
| LLaVA-V1.6-34B       | 8.8           | 5.4             | 1.8           | 12.6           | 6.5            | 4.2           | 4.0            | 6.5            | 3.8           | 5.8              |
| InternVL-4B-Chat-1.5 | 18.5          | 10.7            | 1.8           | 12.5           | 11.1           | 11.9          | 11.4           | 12.3           | 5.5           | 11.6             |
| Qwen-VL-Max          | 14.5          | 11.2            | 3.6           | 16.2           | 1.1            | 11.3          | 11.0           | 12.5           | 10.5          | 11.4             |
| Gemini-Pro-V         | 19.3          | 8.2             | 0.0           | 1.5            | 7.4            | 11.5          | 10.4           | 10.6           | 7.1           | 9.7              |
| Claude-3-Opus        | 29.5          | 19.3            | 3.6           | 32.5           | 16.4           | 23.0          | 20.6           | 21.7           | 16.9          | 20.3             |
| GPT-4V               | 37.8          | 21.2            | 1.8           | 28.7           | 17.9           | 28.0          | 22.2           | 24.7           | 19.5          | 23.1             |
| GPT-4o               | 45.8 | 30.0   | 10.9 | 40.0  | 26.0  | 36.0 | 30.7  | 33.7  | 26.2 | 31.8    |









<!-- <a name="how-to-evaluate-on-MM-MATH"></a>
## ⚙️ How to evaluate on MM-Math -->



#### Data Format

All data in **MM-Math**  are standardized to the following format:

```json
{
    "question": "The text of each question statement conforms to LaTeX code.",
    "image_file_name": "The folder where the question image is located.",
    "image": "The names of the question images in the image folder.",
    "solution": "The text of each question' soluation conforms to LaTeX code.",
    "solution_image": "The image names of solution used in the image folder.",
    "year": "The grade level annotated from each year examination.",
    "difficult": "The difficult level annotated by  examination scores.",
    "knowledge": "Each knowledge points contained in the question, which is annotated by middle school teacher."
}
```



<a name="citation"></a>
## 📝 Citation
```
@article{bai2023longbench,
  title={LongBench: A Bilingual, Multitask Benchmark for Long Context Understanding},
  author={Bai, Yushi and Lv, Xin and Zhang, Jiajie and Lyu, Hongchang and Tang, Jiankai and Huang, Zhidian and Du, Zhengxiao and Liu, Xiao and Zeng, Aohan and Hou, Lei and Dong, Yuxiao and Tang, Jie and Li, Juanzi},
  journal={arXiv preprint arXiv:2308.14508},
  year={2023}
}
```
When citing our work, please kindly consider citing the original dataset papers. The relevant citation information is listed [here](refs/ref.bib).
