
# Set Up

# Specific Charts

## Bar Chart

### Simple Horizontal Bar Chart

```
chart_name <- data %>%
  ggplot(aes(x = reorder(Policy, order), y = Count, fill = Policy)) +
  geom_col() +
  scale_fill_manual(values = cols, name = "Cylinders") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        text = element_text(family = "Palatino")) +
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
```
<details>
  <summary><b>Black and white version</b></summary>
  ```
  b_w_axis <- policy %>%
  ggplot(aes(x = reorder(Policy, order), y = Count, fill = Policy)) +
  geom_col() +
#  geom_text(aes(label = Count), vjust = -0.5) +
  scale_x_discrete(labels = function(x) str_wrap(x, width = 20)) +
  scale_fill_manual(values = b_w, name = "Cylinders") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        axis.line.x = element_line(colour = "black", linewidth = 0.2),
        axis.line.y = element_line(colour = "black", linewidth = 0.2),
        text = element_text(family = "Palatino")) +
  labs(x = "Institution Policy", y = "Number of Universities", title = "Institution-Wide AI Policy at Top 100 U.S. Universities")
    ```
</details>

## Scatter Plot

## Pie Chart

```
pie_data %>%
ggplot(aes(x="", y = percentage_variable, fill=reorder(x_variable, count))) +
geom_bar(stat="identity", width=4, color = "white") +
coord_polar("y", start=0) +
theme_void() +
scale_fill_manual(name = "", values = x_variable_color) +
geom_text(data = subset(data_gen, percent >= 10), # only makes labels for percentages greater than 10%
    aes(label = paste0(percent, "%")), # adds a % sign after the number, not always necessary
    position = position_stack(vjust = 0.6), # adjust to 'float' labels into proper position
    family = "Palatino", size = 5, color = "black") +
labs(title = "title") +
theme(text = element_text(family = "Palatino", size = 12), plot.title = element_text(vjust = -2))

```


## Tree Plot

```
tree_data %>%
ggplot(aes(area = count, fill = school, label = school_clean)) +
geom_treemap(colour = "white", size = 4) +
scale_fill_manual(values = cols_trees, name = "School") +
geom_treemap_text(aes(label = percent, family = "Palatino", place = "topleft", size = 20, reflow = TRUE, padding.x = grid::unit(3, "mm"), padding.y = unit(13, "mm")) +
theme_minimal() +
labs(title = "Percent of TSL Staff from Each College") +
theme(legend.position = "none",
text = element_text(family = "Palatino"),
plot.title = element_text(size = 20))
```

## Line Plot


# Saving and Exporting

