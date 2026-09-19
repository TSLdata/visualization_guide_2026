
# Set Up

# Specific Charts

## Bar Chart

### Simple Horizontal Bar Chart

```
color_viz <- policy %>%
  ggplot(aes(x = reorder(Policy, order), y = Count, fill = Policy)) +
  geom_col() +
#  geom_text(aes(label = Count), vjust = -0.5) +
  scale_x_discrete(labels = function(x) str_wrap(x, width = 20)) +
  scale_fill_manual(values = cols, name = "Cylinders") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        text = element_text(family = "Palatino")) +
  labs(x = "Institution Policy", y = "Number of Universities", title = "Institution-Wide AI Policy at Top 100 U.S. Universities")

color_viz
```
<details>
  <summary><b>Click here to expand</b></summary>
<details>

## Scatter Plot

## Pie Chart

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

