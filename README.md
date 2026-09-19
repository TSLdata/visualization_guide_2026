
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

## Tree Plot

## Line Plot


# Saving and Exporting

